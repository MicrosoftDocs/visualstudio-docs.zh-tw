---
title: 命令執行 |Microsoft Docs
description: 瞭解 Visual Studio 中的命令實行、如何在 VSPackage 中設定命令群組、在其中新增命令、註冊命令，並加以執行。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2031fd74a10c8725157908eaa906c1963a477526
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940107"
---
# <a name="command-implementation"></a>命令執行
若要在 VSPackage 中執行命令，您必須執行下列工作：

1. 在 *.vsct* 檔案中，設定命令群組，然後在其中新增命令。 如需詳細資訊，請參閱 [Visual Studio 命令表格 (. .vsct) ](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔。

2. 向 Visual Studio 註冊命令。

3. 執行命令。

下列各節說明如何註冊和執行命令。

## <a name="register-commands-with-visual-studio"></a>使用 Visual Studio 註冊命令
 如果您的命令要出現在功能表上，您必須將新增 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 至 VSPackage，並使用做為功能表名稱或其資源識別碼的值。

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 此外，您必須向註冊命令 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 。 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>如果您的 VSPackage 衍生自，您就可以使用方法來取得這項服務 <xref:Microsoft.VisualStudio.Shell.Package> 。

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

## <a name="implement-commands"></a>執行命令
 有幾種方式可以執行命令。 如果您想要靜態功能表命令，也就是一律以相同方式顯示的命令，而且在相同的功能表上，請依照 <xref:System.ComponentModel.Design.MenuCommand> 上一節中的範例所示，使用來建立命令。 若要建立靜態命令，您必須提供負責執行命令的事件處理常式。 因為此命令一律為啟用狀態，所以您不需要將其狀態提供給 Visual Studio。 如果您想要根據特定條件來變更命令的狀態，您可以將命令建立為類別的實例， <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 並在其函式中提供事件處理常式來執行命令，以及在 `QueryStatus` 命令的狀態變更時通知 Visual Studio 處理常式。 您也可以將 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 作為命令類別的一部分來執行，或者， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 如果您要將命令提供為專案的一部分，則可以執行。 這兩個介面和 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 類別都有方法可通知 Visual Studio 命令狀態的變更，以及其他提供命令執行的方法。

 當命令新增至命令服務時，它會變成其中一個命令鏈。 當您針對命令執行狀態通知和執行方法時，請務必只提供該特定命令，並將所有其他案例傳遞給鏈中的其他命令。 如果您無法在 (上傳遞命令，通常是藉由傳回 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>) ，Visual Studio 可能會停止正常運作。

## <a name="querystatus-methods"></a>QueryStatus 方法
 如果您要執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 方法，請檢查命令所屬之命令集的 GUID 和命令的識別碼。 請遵循這些方針：

- 如果無法辨識 GUID，您的任何一種方法的執行都必須傳回 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> 。

- 如果任何一個方法的執行都能辨識 GUID，但卻未執行此命令，則方法應該會傳回 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> 。

- 如果您的兩個方法都能辨識 GUID 和命令，則方法應該 `prgCmds` 使用下列旗標，在參數) 中設定每個命令 (的命令旗標欄位 <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> ：

  - `OLECMDF_SUPPORTED`：支援的命令。

  - `OLECMDF_INVISIBLE`：命令不應該是可見的。

  - `OLECMDF_LATCHED`：命令會切換為開啟狀態，並顯示為已核取。

  - `OLECMDF_ENABLED`：命令已啟用。

  - `OLECMDF_DEFHIDEONCTXTMENU`：如果命令出現在快捷方式功能表上，則應該隱藏該命令。

  - `OLECMDF_NINCHED`：命令是功能表控制器，但未啟用，但它的下拉式功能表清單不是空的，而且仍可使用。  (此旗標很少使用。 ) 

- 如果命令是在 *.vsct* 檔案中以旗標定義 `TextChanges` ，請設定下列參數：

  - 將 `rgwz` 參數的元素設定 `pCmdText` 為命令的新文字。

  - 將 `cwActual` 參數的元素設定 `pCmdText` 為命令字串的大小。

此外，請確定目前的內容不是 automation 函式，除非您的命令是專門用來處理 automation 函數。

若要指出您支援特定的命令，請返回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 。 若為所有其他命令，會傳回 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> 。

在下列範例中， `QueryStatus` 方法會先確定內容不是 automation 函式，然後尋找正確的命令集 GUID 和命令識別碼。 命令本身會設定為 [已啟用] 和 [已支援]。 不支援其他命令。

```csharp
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
 方法的執行 `Exec` 類似于方法的執行 `QueryStatus` 。 首先，請確定內容不是 automation 函數。 然後，測試 GUID 和命令識別碼。 如果無法辨識 GUID 或命令識別碼，就會傳回 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> 。

 若要處理命令，請執行此命令，並 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 在執行成功時傳回。 您的命令負責錯誤偵測和通知;因此，如果執行失敗，則傳回錯誤碼。 下列範例示範如何執行執行方法。

```csharp
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

- [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
