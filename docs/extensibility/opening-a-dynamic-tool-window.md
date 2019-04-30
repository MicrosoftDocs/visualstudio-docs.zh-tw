---
title: 開啟動態工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e45d6cadbc74ddcc7b46ee53d2d8cdc8cce63a47
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434225"
---
# <a name="open-a-dynamic-tool-window"></a>開啟動態工具視窗
從上一個功能表或對等的鍵盤快速鍵的命令通常開啟的工具視窗。 有些時候，不過，您可能需要特定的 UI 內容套用，而關閉時的 UI 內容不再適用時，便會開啟工具視窗。 工具視窗的這些類型稱為*動態*或是*自動顯示*。

> [!NOTE]
> 如需預先定義的 UI 內容，請參閱<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>。

 如果您想要開啟動態工具視窗，在啟動時，而且可能建立失敗，您必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx>介面，並測試中的失敗狀況<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A>方法。 為了讓命令介面知道有應該在啟動時開啟動態工具視窗，您必須新增`SupportsDynamicToolOwner`套件登錄值 （設定為 1）。 此值不是標準的一部分<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>，因此您必須建立自訂的屬性，將它加入。 如需有關自訂屬性的詳細資訊，請參閱 <<c0> [ 使用自訂註冊屬性來登錄延伸模組](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension)。

 使用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>開啟工具視窗。 視需要建立工具視窗。

> [!NOTE]
> 使用者可以關閉動態工具視窗。 如果您想要建立功能表命令，讓使用者可以重新開啟工具視窗時，應該在相同的 UI 內容，以開啟工具視窗中，以及已停用其他方式啟用功能表命令。

## <a name="to-open-a-dynamic-tool-window"></a>若要開啟動態工具視窗

1. 建立 VSIX 專案，名為**DynamicToolWindow** ，並新增名為的工具視窗項目範本*DynamicWindowPane.cs*。 如需詳細資訊，請參閱 <<c0> [ 建立的擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。

2. 在  *DynamicWindowPanePackage.cs*檔案中，尋找 DynamicWindowPanePackage 宣告。 新增<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>註冊工具視窗的屬性。

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

     前述屬性註冊為暫時性的視窗，關閉並重新開啟 Visual Studio 時，不會保存命名 DynamicWindowPane 工具視窗。 開啟 DynamicWindowPane 每當<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>套用，而否則關閉。

3. 建置此專案並開始偵錯。 實驗執行個體應該會出現。 您應該不會看到工具視窗。

4. 在實驗執行個體中開啟專案。 工具視窗應該會出現。