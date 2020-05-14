---
title: 命令實現 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709584"
---
# <a name="command-implementation"></a>命令執行
要在 VSPackage 中執行指令,必須執行以下工作:

1. 在 *.vsct*檔中,設定一個命令組,然後將命令添加到該檔中。 有關詳細資訊,請參閱[可視化工作室命令表 (.vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。

2. 向可視化工作室註冊該命令。

3. 實現命令。

以下各節說明如何註冊和實現命令。

## <a name="register-commands-with-visual-studio"></a>在視覺化工作室註冊命令
 如果命令要顯示在選單上,則必須<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>將添加到 VSPackage,並將功能表的名稱或其資源 ID 用作值。

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 此外,必須向註冊<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>命令。 如果 VSPackage 派<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A><xref:Microsoft.VisualStudio.Shell.Package>生自 ,則可以使用 方法獲取此服務。

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

## <a name="implement-commands"></a>執行指令
 實現命令的方法有很多種。 如果需要靜態功能表命令(該命令是始終以相同方式顯示的命令,並且在同一功能表上)使用,請使用<xref:System.ComponentModel.Design.MenuCommand>上一節中的示例中所示創建該命令。 要創建靜態命令,必須提供負責執行該命令的事件處理程式。 由於該命令始終處於啟用狀態且可見,因此您不必向 Visual Studio 提供其狀態。 如果要根據特定條件更改命令的狀態,則可以將該命令創建為<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類的實例,並在其構造函數中提供事件處理程式來執行命令,並提供一`QueryStatus`個 處理程式,以便在命令的狀態更改時通知 Visual Studio。 還可以作為命令類<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>的一部分實現,或者,如果作為專案的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>一部分提供命令,則可以實現。 兩個介面和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>類都有通知 Visual Studio 命令狀態更改的方法,以及提供執行命令的其他方法。

 將命令添加到命令服務時,該命令將成為命令鏈之一。 實現命令的狀態通知和執行方法時,請注意僅提供該特定命令,並將所有其他情況傳遞給鏈中的其他命令。 如果您未能傳遞命令(通常是返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>),Visual Studio 可能會停止正常工作。

## <a name="querystatus-methods"></a>查詢狀態方法
 如果要實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>方法,請檢查命令所屬的命令集的 GUID 和命令的 ID。 請遵循這些方針：

- 如果識別 GUID,則任一方法的實現都必須<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>返回 。

- 如果任一方法的實現都識別 GUID,但尚未實現該命令,則該方法應<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>返回 。

- 如果任一方法的實現同時識別 GUID 和指令,則該方法應`prgCmds`<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>使用以下 標誌設定每個命令(在參數中)的命令標誌欄位:

  - `OLECMDF_SUPPORTED`:該命令受支援。

  - `OLECMDF_INVISIBLE`:該命令不應可見。

  - `OLECMDF_LATCHED`: 命令已切換,似乎已選中。

  - `OLECMDF_ENABLED`:命令已啟用。

  - `OLECMDF_DEFHIDEONCTXTMENU`:如果命令出現在快捷菜單上,則應隱藏該命令。

  - `OLECMDF_NINCHED`:該命令是功能表控制器,未啟用,但其下拉菜單清單不為空,仍然可用。 (此標誌很少使用。

- 如果命令是在帶`TextChanges`旗標的 *.vsct*檔中定義的,則設定以下參數:

  - 將`rgwz``pCmdText`參數的元素設定為命令的新文本。

  - 將`cwActual``pCmdText`參數的元素設定為命令字串的大小。

此外,請確保當前上下文不是自動化函數,除非您的命令專門用於處理自動化函數。

要指示您支援特定指令,請傳<xref:Microsoft.VisualStudio.VSConstants.S_OK>回 。 對所有其他指令,傳<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>回 。

在下面的範例中,`QueryStatus`該方法首先確保上下文不是自動化函數,然後找到正確的命令集 GUID 和命令 ID。 命令本身設置為啟用和支援。 不支援其他命令。

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
 `Exec`方法的實現類似於方法的`QueryStatus`實現。 首先,請確保上下文不是自動化函數。 然後,測試 GUID 和命令 ID。 如果無法識別 GUID 或指令<xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>代碼, 則傳回 。

 要處理該命令,請執行該命令<xref:Microsoft.VisualStudio.VSConstants.S_OK>,並在執行成功時返回。 您的命令負責錯誤檢測和通知;因此,如果執行失敗,則返回錯誤代碼。 下面的示例演示如何實現執行方法。

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

- [VS 套件如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
