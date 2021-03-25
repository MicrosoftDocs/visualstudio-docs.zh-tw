---
title: 開啟動態工具視窗 |Microsoft Docs
description: 瞭解動態工具視窗，此視窗會在 UI 內容不再適用時，每次有特定 UI 內容套用並關閉時開啟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 357644f67da9a3bbc468d708cf39e44f737dbf0f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090417"
---
# <a name="open-a-dynamic-tool-window"></a>開啟動態工具視窗
通常會從功能表上的命令或對等的鍵盤快速鍵開啟工具視窗。 但有時候，您可能需要在每次套用特定 UI 內容時開啟的工具視窗，並在不再套用 UI 內容時關閉。 這些類型的工具視窗稱為 *動態* 或 *自動顯示*。

> [!NOTE]
> 如需預先定義的 UI 內容清單，請參閱 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 。

 如果您想要在啟動時開啟動態工具視窗，而且可能會導致建立失敗，您必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> 介面並測試方法中的失敗狀況 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> 。 為了讓 shell 知道您有一個應該在啟動時開啟的動態工具視窗，您必須將 `SupportsDynamicToolOwner` (設定為 1) 的值新增至您的套件註冊。 此值不是標準的一部分 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> ，因此您必須建立自訂屬性以將它加入。 如需自訂屬性的詳細資訊，請參閱 [使用自訂註冊屬性註冊擴充](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)功能。

 使用 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 開啟工具視窗。 您可以視需要建立工具視窗。

> [!NOTE]
> 使用者可以關閉動態工具視窗。 如果您想要建立功能表命令，讓使用者可以重新開啟工具視窗，則應該在開啟工具視窗的相同 UI 內容中啟用功能表命令，否則會停用。

## <a name="to-open-a-dynamic-tool-window"></a>開啟動態工具視窗

1. 建立名為 **DynamicToolWindow** 的 VSIX 專案，並加入名為 *DynamicWindowPane* 的工具視窗專案範本。 如需詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

2. 在 *DynamicWindowPanePackage .cs* 檔案中，尋找 DynamicWindowPanePackage 宣告。 新增 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> 屬性以註冊工具視窗。

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

     上述屬性會將名為 DynamicWindowPane 的工具視窗註冊為暫時性視窗，當 Visual Studio 關閉並重新開啟時，不會保存該視窗。 DynamicWindowPane 會在每次套用時開啟 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ，否則會關閉。

3. 建置此專案並開始偵錯。 實驗實例應會出現。 您應該不會看到工具視窗。

4. 在實驗實例中開啟專案。 應該會出現工具視窗。
