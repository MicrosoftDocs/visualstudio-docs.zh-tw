---
title: "命令實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2704794e4683fb461dca971a3893ca831591ca0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="command-implementation"></a>命令的實作
若要在 VSPackage 中實作的命令，您必須執行下列工作：  
  
1.  在.vsct 檔案中，設定命令群組並將命令新增到它。 如需詳細資訊，請參閱[Visual Studio 命令表 (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  向 Visual Studio 中的命令。  
  
3.  實作命令。  
  
 下列各節說明如何註冊和實作命令。  
  
## <a name="registering-commands-with-visual-studio"></a>使用 Visual Studio 註冊命令  
 如果您的命令就是出現在功能表上，您必須新增<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>至您的 VSPackage，並使用做為值的功能表名稱，或是其資源識別碼。  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 此外，您必須註冊命令與<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。 您可以使用來取得這項服務<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>方法，如果您的 VSPackage 衍生自<xref:Microsoft.VisualStudio.Shell.Package>。  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>實作命令  
 有數種方式來實作命令。 如果您想要靜態功能表命令，也就是一律會顯示相同方式，在相同的功能表上的命令，此命令使用建立<xref:System.ComponentModel.Design.MenuCommand>上一節中的範例所示。 若要建立靜態的命令，您必須提供事件處理常式負責執行命令。 命令一定是啟用的可見的因為您沒有 Visual studio 提供其狀態。 如果您想要變更命令，以根據特定條件的狀態，您可以建立命令的執行個體<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類別，並在其建構函式，提供事件處理常式執行的命令和查詢狀態處理常式以通知 VisualStudio 命令的狀態變更時。 您也可以實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令類別或部分，您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>如果您提供的命令為專案的一部分。 將兩個介面和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>所有類別都具有方法告知 Visual Studio 中的變更命令的狀態，以及提供執行此命令的其他方法。  
  
 當命令會新增至命令服務時，它會變成的命令鏈結的其中一個。 當您實作命令的狀態通知和執行方法時，小心只針對該特定命令提供以及鏈結中傳遞至其他命令的其他所有情況。 如果您無法將傳遞命令 (通常是藉由傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)，Visual Studio 可能會停止正常運作。  
  
## <a name="query-status-methods"></a>查詢狀態方法  
 如果您要實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>方法中，檢查設定所屬命令的命令的 GUID 和命令的識別碼。 請遵循這些方針：  
  
-   如果無法辨識的 GUID，這兩種方法的實作必須傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
-   如果您實作任一種方法可辨識的 GUID，但尚未實際實作命令，則這個方法應傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
-   如果您實作任一種方法可辨識的 GUID，以及命令，則方法應該設定的每個命令的命令旗標 欄位 (在`prgCmds`參數) 使用下列旗標：  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果支援該命令。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果命令不應該為可見的。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果命令切換為開，而且似乎已檢查。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果已啟用命令。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果應該隱藏命令，如果它是顯示在快顯功能表。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果命令功能表控制器，且未啟用，但其下拉式選單清單不是空白，且仍可使用。 （這個旗標會很少使用）。  
  
-   如果命令定義在.vsct 檔使用`TextChanges`旗標，請設定下列參數：  
  
    -   設定`rgwz`元素`pCmdText`新命令文字的參數。  
  
    -   設定`cwActual`元素`pCmdText`命令字串的大小參數。  
  
 也請確定目前的內容不是自動化函式，除非您的命令特別設計用來處理 automation 函式。  
  
 若要指出，可以支援特定的命令，傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 對於所有其他的命令傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
 在下列範例中，查詢狀態方法會先確定內容不是自動化函式，則會尋找正確的命令集 GUID 和命令 id。 命令本身會設定為啟用，而且支援。 沒有其他命令的支援。  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>執行方法  
 執行方法的實作類似於查詢狀態方法的實作。 首先，請確定您的內容不是自動化函式。 然後測試 GUID 和命令 id。 如果 GUID 或無法辨認命令 ID，傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
 若要處理命令，執行它，並傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>如果執行成功。 您的命令會負責錯誤偵測與通知;如果執行作業失敗，因此，傳回錯誤碼。 下列範例會示範實作執行方法的方式。  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>請參閱  
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)