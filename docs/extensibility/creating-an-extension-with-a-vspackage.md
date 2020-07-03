---
title: 使用 VSPackage 建立擴充功能 |Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68ade2f8d334c1f93349e396d910fa300f6b5417
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903856"
---
# <a name="create-an-extension-with-a-vspackage"></a>使用 VSPackage 建立擴充功能

本逐步解說會示範如何建立 VSIX 專案，以及如何新增 VSPackage 專案專案。 我們將使用 VSPackage 來取得 UI Shell 服務，以便顯示訊息方塊。

## <a name="prerequisites"></a>必要條件

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vspackage"></a>建立 VSPackage

1. 建立名為**FirstPackage**的 VSIX 專案。 藉由搜尋「vsix」，您可以在 [**新增專案**] 對話方塊中尋找 VSIX 專案範本。

2. 當專案開啟時，新增名為**FirstPackage**的 Visual Studio 封裝專案範本。 在 [**方案總管**中，以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **新專案**]。 在 [**加入新專案**] 對話方塊中，移至 [ **Visual c #** 擴充性]，  >  **Extensibility**然後選取 [ **Visual Studio 封裝**]。 在視窗底部的 [**名稱**] 欄位中，將命令檔名稱變更為*FirstPackage.cs*。

3. 建置此專案並開始偵錯。

    Visual Studio 的實驗實例隨即出現。 如需實驗實例的詳細資訊，請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

4. 在實驗實例中，開啟 [**工具**  >  ] [**擴充功能和更新**] 視窗。 您應該會在這裡看到**FirstPackage**延伸模組。 （如果您在 Visual Studio 的工作實例中開啟 [**擴充功能和更新**]，就不會看到 [ **FirstPackage**]）。

## <a name="load-the-vspackage"></a>載入 VSPackage

此時，不會載入延伸模組，因為沒有任何動作會導致載入。 當您與 UI 互動時（按一下功能表命令、開啟工具視窗），或指定 VSPackage 應該載入特定的 UI 內容時，通常可以載入擴充功能。 如需載入 Vspackage 和 UI 內容的詳細資訊，請參閱[載入 vspackage](../extensibility/loading-vspackages.md)。 在此程式中，我們將示範如何在開啟方案時載入 VSPackage。

1. 開啟*FirstPackage.cs*檔案。 尋找類別的宣告 `FirstPackage` 。 將現有的屬性取代為下列屬性：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. 讓我們新增一則訊息，讓我們知道已載入 VSPackage。 我們會使用 VSPackage 的 `Initialize()` 方法來執行這件事，因為您只能在 VSPackage 被放置之後，取得 Visual Studio 的服務。 （如需有關取得服務的詳細資訊，請參閱[如何：取得服務](../extensibility/how-to-get-a-service.md)）。`Initialize()` `FirstPackage` 以取得服務的程式碼取代的方法 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 、取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，並呼叫其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 方法。

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

4. 在實驗實例中開啟方案。 您應該會看到一個訊息方塊，指出**Initialize （）內的第一個封裝**。
