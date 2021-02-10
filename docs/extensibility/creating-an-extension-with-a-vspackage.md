---
title: 使用 VSPackage 建立延伸模組 |Microsoft Docs
description: 瞭解如何使用 VSPackage 建立 VSIX 專案並加入 VSPackage 專案專案，以取得 UI Shell 服務，以便顯示訊息方塊。
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b847fad9752c6a2448c0fdc571815ea1823e2d9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944891"
---
# <a name="create-an-extension-with-a-vspackage"></a>使用 VSPackage 建立延伸模組

本逐步解說將示範如何建立 VSIX 專案並加入 VSPackage 專案專案。 我們將使用 VSPackage 來取得 UI Shell 服務，以便顯示訊息方塊。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vspackage"></a>建立 VSPackage

1. 建立名為 **FirstPackage** 的 VSIX 專案。 您可以藉由搜尋 "vsix"，在 [ **新增專案** ] 對話方塊中找到 VSIX 專案範本。

2. 當專案開啟時，加入名為 **FirstPackage** 的 Visual Studio 套件專案範本。 在 [**方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  然後選取 [ **Visual Studio 套件**]。 在視窗底部的 [ **名稱** ] 欄位中，將命令檔名稱變更為 *FirstPackage.cs*。

3. 建置此專案並開始偵錯。

    Visual Studio 的實驗實例隨即出現。 如需實驗實例的詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。

4. 在實驗實例中，開啟 [**工具**  >  **擴充功能和更新**] 視窗。 您應該會在這裡看到 **FirstPackage** 延伸模組。  (如果您在 Visual Studio 的工作實例中開啟 [ **擴充功能和更新** ]，就不會看到 **FirstPackage**) 。

## <a name="load-the-vspackage"></a>載入 VSPackage

此時不會載入擴充功能，因為沒有任何專案會造成載入。 當您與 UI 互動時，通常可以載入擴充功能 (按一下功能表命令、開啟工具視窗) ，或指定 VSPackage 應該在特定的 UI 內容中載入。 如需有關載入 Vspackage 和 UI 內容的詳細資訊，請參閱 [載入 vspackage](../extensibility/loading-vspackages.md)。 在此程式中，我們將示範如何在解決方案開啟時載入 VSPackage。

1. 開啟 *FirstPackage.cs* 檔案。 尋找類別的宣告 `FirstPackage` 。 將現有屬性取代為下列屬性：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. 讓我們新增一則訊息，讓我們知道 VSPackage 已經載入。 我們會使用 VSPackage 的 `Initialize()` 方法來執行此動作，因為您只能在 VSPackage 已放置之後取得 Visual Studio 服務。  (如需取得服務的詳細資訊，請參閱 [如何：取得](../extensibility/how-to-get-a-service.md)服務。 ) 將的 `Initialize()` 方法取代 `FirstPackage` 為取得服務的程式碼 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 、取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，以及呼叫其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 方法。

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. 建置此專案並開始偵錯。 實驗實例隨即出現。

4. 在實驗實例中開啟方案。 您應該會看到一個訊息方塊，指出 **初始化 ( # B1 內的第一個封裝**。
