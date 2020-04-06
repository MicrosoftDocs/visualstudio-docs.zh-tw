---
title: 開啟動態工具視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702266"
---
# <a name="open-a-dynamic-tool-window"></a>開啟動態工具視窗
工具視窗通常從功能表上的命令或等效的鍵盤快捷鍵打開。 但是,有時您可能需要一個工具視窗,該視窗在應用特定 UI 上下文時打開,並在 UI 上下文不再應用時關閉。 這些型態的工具視窗是*動態*或*自動可見*。

> [!NOTE]
> 有關預先定義的 UI 中選文的清單<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>,請參閱 。

 如果要在啟動時打開動態工具視窗,並且創建可能失敗,則必須實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx>介面並測試方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A>中的 失敗條件。 為了使 shell 知道在啟動時應打開的動態工具視窗,`SupportsDynamicToolOwner`必須將值(設置為 1)添加到包註冊中。 此值不是標準的<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>一部分,因此必須創建自定義屬性來添加它。 有關自訂屬性的詳細資訊,請參閱[使用自訂註冊屬性註冊擴展](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)。

 用於<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>打開工具視窗。 根據需要創建工具視窗。

> [!NOTE]
> 用戶可以關閉動態工具視窗。 如果要創建功能表命令以便用戶可以重新打開工具視窗,則應在打開工具視窗的相同 UI 上下文中啟用選單命令,否則將禁用該命令。

## <a name="to-open-a-dynamic-tool-window"></a>開啟動態工具視窗

1. 創建名為**DynamicToolWindow 的**VSIX 專案,並添加名為*DynamicWindowPane.cs*的工具視窗項範本。 關於詳細資訊,請參閱[使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)。

2. 在*DynamicWindowPanePackage.cs*檔中,尋找動態視窗窗格包聲明。 添加<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>屬性以註冊工具視窗。

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     上述屬性將名為 DynamicWindowPane 的工具視窗註冊為瞬態視窗,在 Visual Studio 關閉並重新打開時不會持久化。 動態視窗窗格在應用時<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>打開,否則關閉。

3. 建置此專案並開始偵錯。 應出現實驗實例。 不應看到工具視窗。

4. 在實驗實例中打開專案。 應顯示工具視窗。
