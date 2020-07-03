---
title: 開啟動態工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a06cea6d9de4271572457dc9fe6473b5c969b66
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903706"
---
# <a name="open-a-dynamic-tool-window"></a>開啟動態工具視窗
工具視窗通常是從功能表上的命令或對等的鍵盤快速鍵開啟。 不過，有時候您可能需要一個在特定 UI 內容套用時開啟的工具視窗，當 UI 內容不再適用時，就會關閉。 這些類型的工具視窗稱為「*動態*」或「*自動顯示*」。

> [!NOTE]
> 如需預先定義的 UI 內容清單，請參閱 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 。

 如果您想要在啟動時開啟動態工具視窗，而且可以建立失敗，您必須 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 在方法中執行介面並測試失敗狀況 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> 。 為了讓 shell 知道您有應該在啟動時開啟的動態工具視窗，您必須將 `SupportsDynamicToolOwner` 值（設為1）新增至您的套件註冊。 這個值不是標準的一部分 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> ，因此您必須建立自訂屬性來加入它。 如需自訂屬性的詳細資訊，請參閱[使用自訂註冊屬性來註冊延伸](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)模組。

 使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 來開啟工具視窗。 工具視窗會視需要建立。

> [!NOTE]
> 使用者可以關閉動態工具視窗。 如果您想要建立功能表命令，讓使用者可以重新開啟工具視窗，則應該在開啟工具視窗的相同 UI 內容中啟用功能表命令，否則會停用。

## <a name="to-open-a-dynamic-tool-window"></a>開啟動態工具視窗

1. 建立名為**DynamicToolWindow**的 VSIX 專案，並加入名為*DynamicWindowPane.cs*的工具視窗專案範本。 如需詳細資訊，請參閱[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

2. 在*DynamicWindowPanePackage.cs*檔案中，尋找 DynamicWindowPanePackage 宣告。 加入 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> 屬性以註冊工具視窗。

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

     上述屬性會將名為 DynamicWindowPane 的工具視窗註冊為暫時性視窗，而當 Visual Studio 關閉並重新開啟時，不會保存此視窗。 DynamicWindowPane 會在每次套用時開啟 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ，否則會關閉。

3. 建置此專案並開始偵錯。 應該會出現實驗實例。 您不應該看到工具視窗。

4. 在實驗實例中開啟專案。 工具視窗應該會隨即出現。
