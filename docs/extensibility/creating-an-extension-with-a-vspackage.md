---
title: 使用 VS 套件建立延伸 :微軟文件
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739534"
---
# <a name="create-an-extension-with-a-vspackage"></a>使用 VS 套件建立延伸

本演練將介紹如何建立 VSIX 專案並添加 VSPackage 專案項。 我們將使用 VSPackage 獲取 UI Shell 服務,以便顯示訊息框。

## <a name="prerequisites"></a>Prerequisites

從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-vspackage"></a>建立 VS 套件

1. 創建名為 **"第一包"的**VSIX 專案。 您可以通過搜尋"vsix"在 **"新項目**"對話框中找到 VSIX 專案範本。

2. 打開專案時,添加名為**FirstPackage**的可視化工作室包項範本。 在**解決方案資源管理器**中,右鍵單擊專案節點並選擇「**添加新** > **項**」。 在 **'新增新項目'** 對話框中,轉到**視覺化 C#** > **可擴充性**並選擇**視覺化工作室套件**。 在視窗底部的**名稱「 欄**位中」,將指令檔名變更為*FirstPackage.cs*。

3. 建置此專案並開始偵錯。

    視覺工作室的實驗實例出現。 有關實驗實例的詳細資訊,請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

4. 在實驗例中,打開 **「工具** > **擴展」和「更新」** 視窗。 您應該在此處查看**第一個包**擴展。 (如果在 Visual Studio 的工作實例中打開**擴展和更新**,則看不到**第一包**)。

## <a name="load-the-vspackage"></a>載入 VS 套件

此時,擴展不會載入,因為沒有任何內容導致它載入。 通常,在與其 UI 互動時(單擊功能表命令、打開工具視窗)或指定 VSPackage 應在特定 UI 上下文中載入時,可以載入擴展。 有關載入 VS 套件和 UI 的詳細資訊,請參閱[載入 VS 套件](../extensibility/loading-vspackages.md)。 對於此過程,我們將向您展示如何在打開解決方案時載入 VSPackage。

1. 打開*FirstPackage.cs*檔。 尋找類別的聲明`FirstPackage`。 將現有屬性取代為以下屬性:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. 讓我們添加一條消息,讓我們知道 VS 包已載入。 我們使用 VSPackage`Initialize()`的方法執行此操作,因為只有在 VSPackage 已點位後,才能獲得 Visual Studio 服務。 (有關取得服務的詳細資訊,請參閱[如何:取得服務](../extensibility/how-to-get-a-service.md)。`Initialize()`將`FirstPackage`方法替換為獲取<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>獲取 介面並調<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>用其 方法的代碼。

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

3. 建置此專案並開始偵錯。 出現實驗實例。

4. 在實驗實例中打開解決方案。 您應該會看到一個訊息框,其中顯示**第一個包初始化()**。
