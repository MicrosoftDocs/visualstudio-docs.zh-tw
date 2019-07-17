---
title: 命令實作 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195064"
---
# <a name="command-implementation"></a>命令實作
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

若要在 VSPackage 中實作的命令，您必須執行下列工作：  
  
1. 在.vsct 檔案中，設定命令群組，並接著將命令加入至它。 如需詳細資訊，請參閱[Visual Studio Command Table (。Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. 向 Visual Studio 中的命令。  
  
3. 實作命令。  
  
   下列各節說明如何註冊及實作命令。  
  
## <a name="registering-commands-with-visual-studio"></a>向 Visual Studio 中的命令  
 如果您的命令就會出現在功能表上，您必須新增<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>到您的 VSPackage，並使用做為值的功能表名稱或其資源識別碼。  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 此外，您必須註冊命令並搭配<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。 您可以使用，以取得此服務<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>方法，如果 VSPackage 衍生自<xref:Microsoft.VisualStudio.Shell.Package>。  
  
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
 有數種方式來實作命令。 如果您想要靜態功能表命令，也就是一律會顯示相同方式，且在相同的功能表上的命令，此命令使用建立<xref:System.ComponentModel.Design.MenuCommand>上一節中的範例所示。 若要建立靜態的命令，您必須提供事件處理常式負責執行命令。 命令一律為已啟用並為可見的因為您沒有 Visual studio 提供它的狀態。 如果您想要變更命令，以根據特定條件的狀態，您可以建立命令的執行個體為<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類別，並在其建構函式，提供事件處理常式執行的命令和通知視覺效果的查詢狀態處理常式Studio 命令的狀態變更時。 您也可以實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>因為命令類別或部分，您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>如果您要為專案的一部分提供的命令。 兩個介面和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類別的所有已通知 Visual Studio 中的命令狀態的變更的方法和其他方法，可提供執行命令。  
  
 當命令加入至命令服務時，它會變成的一連串命令的其中一個。 當您實作命令的狀態通知和執行方法時，負責提供只會針對該特定命令，以及傳遞至其他命令的其他所有情況下，鏈結中。 如果您無法傳遞命令 (通常是藉由傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)，Visual Studio 可能會停止正常運作。  
  
## <a name="query-status-methods"></a>查詢狀態方法  
 如果您要實作其中一個<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>方法中，檢查的命令集命令所屬的 GUID 和命令的識別碼。 請遵循這些方針：  
  
- 如果無法辨識的 GUID，這兩種方法的實作必須傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
- 如果這兩種方法的實作可辨識的 GUID，但尚未實際實作命令，則這個方法應傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
- 如果這兩種方法的實作會辨識 GUID 和命令，則方法應該設定的每個命令的命令旗標 欄位 (在`prgCmds`參數) 使用下列旗標：  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 如果支援該命令。  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 如果命令不應該為可見的。  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 如果命令切換開啟，而且似乎已檢查。  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 如果此命令會啟用。  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 如果應該隱藏命令，如果出現在捷徑功能表。  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 如果命令功能表控制器，且未啟用，但它的下拉式選單清單不是空的以及仍然可用。 （這個旗標是很少使用）。  
  
- 如果命令已定義在.vsct 檔案中以`TextChanges`旗標，請設定下列參數：  
  
  - 設定`rgwz`項目`pCmdText`新命令文字的參數。  
  
  - 設定`cwActual`項目`pCmdText`命令字串的大小參數。  
  
  也請確定目前的內容不是自動化函式中，除非處理自動化函式，而且特別適合您的命令。  
  
  若要指出您是否支援特定的命令，傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 如需其他命令，傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
  在下列範例中，查詢狀態方法第一次可確保內容不是自動化函式，則會尋找正確的命令集 GUID 和命令識別碼。 命令本身會設定為啟用，而且支援。 支援不含其他命令。  
  
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
 在執行方法的實作類似於查詢狀態; 方法的實作。 首先，請確定內容不是自動化函式。 然後測試 GUID 和命令 id。 如果 GUID 或無法辨認命令 ID，傳回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
 若要處理的命令，執行它，並傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>如果執行成功。 您的命令會負責錯誤偵測和通知;如果執行失敗，因此，傳回錯誤碼。 下列範例會示範實作的執行方法的方式。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
