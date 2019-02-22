---
title: Creating an Extension with VSPackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0f5e7b94c4aa8ff4bcdea88741c8be0319bcc16
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316272"
---
# <a name="create-an-extension-with-a-vspackage"></a>使用 VSPackage 建立擴充功能
本逐步解說會示範如何建立 VSIX 專案，並加入 VSPackage 專案項目。 我們將使用 VSPackage 來取得，UI Shell 服務以顯示訊息方塊。

## <a name="prerequisites"></a>必要條件
從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vspackage"></a>建立 VSPackage

1. 建立 VSIX 專案，名為**FirstPackage**。 您可以找到在 VSIX 專案範本**新的專案**下方的對話方塊**Visual C#** > **擴充性**。

2. 當專案開啟時，新增名為 Visual Studio 封裝項目範本**FirstPackage**。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增** > **新項目**。 在 **加入新項目**對話方塊中，移至**Visual C#** > **擴充性**，然後選取**Visual Studio Package**。 在 **名稱**視窗的底部欄位中，將命令的檔案名稱變更為*FirstPackage.cs*。

3. 建置此專案並開始偵錯。

    Visual Studio 的實驗執行個體隨即出現。 如需詳細的實驗執行個體的詳細資訊，請參閱[實驗的執行個體](../extensibility/the-experimental-instance.md)。

4. 在實驗執行個體中，開啟**工具** > **擴充功能和更新**視窗。 您應該會看到**FirstPackage**延伸模組。 (如果您開啟**擴充功能和更新**在您的 Visual Studio 的工作執行個體，您將不會看到**FirstPackage**)。

## <a name="load-the-vspackage"></a>載入 VSPackage
此時的延伸模組未載入，因為沒有任何會導致它載入。 互動 （按一下功能表命令，開啟 [工具] 視窗），其 UI 或藉由指定特定的 UI 內容中，應該載入 VSPackage 時，您通常可以載入延伸模組。 如需有關載入 Vspackage 和 UI 內容的詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。 此程序，我們將示範如何載入 VSPackage，開啟方案時。

1. 開啟*FirstPackage.cs*檔案。 尋找宣告`FirstPackage`類別。 取代下列項目取代現有的屬性：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. 讓我們加入訊息，讓我們知道已載入 VSPackage。 我們使用 VSPackage 的`Initialize()`方法來這樣做，因為您可以取得 Visual Studio 服務已設置 VSPackage 時，才。 (如需有關如何取得服務的詳細資訊，請參閱[How to:取得服務](../extensibility/how-to-get-a-service.md)。)取代`Initialize()`方法`FirstPackage`取得的程式碼<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務，取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面，並呼叫其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>方法。

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

3. 建置此專案並開始偵錯。 實驗執行個體隨即出現。

4. 在實驗執行個體中開啟方案。 您應該會看到出現訊息方塊，指出**第一個套件內 initialize （)**。
