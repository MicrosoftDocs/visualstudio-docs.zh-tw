---
title: 如何：診斷延伸模組效能 |Microsoft Docs
description: Visual Studio 通知較慢擴充功能的使用者。 瞭解如何計算擴充功能的影響，以及如何在本機分析擴充功能的影響。
ms.custom: SEO-VS-2020
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jmartens
ms.workload:
- bertaygu
ms.openlocfilehash: 05dda944ab2aecd429386e0e4c40646d21e9a3d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966405"
---
# <a name="measuring-extension-impact-in-startup"></a>測量擴充功能對啟動的影響

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>專注于 Visual Studio 2017 的延伸模組效能

根據客戶的意見反應，Visual Studio 2017 版本的其中一個焦點區域是啟動和解決方案載入效能。 作為 Visual Studio platform 小組，我們致力於改善啟動和解決方案載入效能。 一般而言，我們的度量建議已安裝的擴充功能也會對這些案例產生相當大的影響。

為了協助使用者瞭解這項影響，我們在 Visual Studio 中新增了一項新功能，以通知較慢延伸的使用者。 有時候，Visual Studio 會偵測到新的擴充功能，以減緩解決方案載入或啟動的速度。 當偵測到速度變慢時，使用者會在 IDE 中看到通知，指向新的 [管理 Visual Studio 效能] 對話方塊。 [說明] 功能表也可以一律存取這個對話方塊，以流覽先前偵測到的延伸模組。

![管理 Visual Studio 效能](media/manage-performance.png)

本檔旨在說明擴充功能的計算方式，以協助擴充開發人員。 本檔也會說明如何在本機分析擴充功能的影響。 本機分析延伸模組影響將會決定延伸模組是否會顯示為影響效能的擴充功能。

> [!NOTE]
> 本檔著重于擴充功能在啟動和載入解決方案時的影響。 擴充功能也會在造成 UI 沒有回應時，影響 Visual Studio 的效能。 如需本主題的詳細資訊，請參閱 [如何：診斷延伸模組造成的 UI 延遲](how-to-diagnose-ui-delays-caused-by-extensions.md)。

## <a name="how-extensions-can-impact-startup"></a>擴充功能可能會如何影響啟動

擴充功能影響啟動效能最常見的方式之一，就是選擇自動載入其中一個已知的啟動 UI 內容，例如 NoSolutionExists 或 ShellInitialized。 這些 UI 內容會在啟動期間啟用。 任何包含 `ProvideAutoLoad` 其定義中具有這些內容之屬性的封裝，都會在該時間載入和初始化。

當我們測量擴充功能的影響時，我們主要著重于這些擴充功能所花費的時間，這些延伸模組會選擇在上述內容中自動載入。 測量的時間會包含但不限於：

* 載入同步封裝的延伸模組元件
* 針對同步封裝在封裝類別的函式中花費的時間
* 封裝初始化所花費的時間 (或同步封裝的 SetSite) 方法
* 針對非同步封裝，上述作業會在背景執行緒上執行。  如此一來，作業就會排除在監視之外。
* 在封裝初始化期間排程于主要執行緒上執行的任何非同步工作所花費的時間
* 事件處理常式中花費的時間，特別是 shell 初始化的內容啟用或 shell 廢止狀態變更
* 從 Visual Studio 2017 Update 3 開始，我們也會在初始化 shell 之前，開始監視在閒置電話上花費的時間。 閒置處理常式中長時間的作業也會導致沒有回應的 IDE，並由使用者貢獻到察覺的啟動時間。

從 Visual Studio 2015 開始，我們已新增許多功能。 這些功能有助於移除封裝自動載入的需求。 這些功能也會延遲封裝載入至更特定案例的需求。 這些案例包含的範例會讓使用者更容易使用延伸模組，或在自動載入時降低擴充功能的影響。

您可以在下列檔中找到這些功能的更多詳細資料：

以[規則為基礎的 ui](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)內容：根據 ui 內容建立更豐富的以規則為基礎的引擎，可讓您根據專案類型、類別和屬性建立自訂內容。 自訂內容可以用來在更明確的情況下載入封裝。 這些特定案例包括具有特定功能的專案，而不是啟動的專案。 自訂內容也可讓您根據專案元件或其他可用詞彙， [將命令可見度系結至自訂內容](visibilityconstraints-element.md) 。 這項功能可讓您不必載入封裝來註冊命令狀態查詢處理常式。

[非同步封裝支援](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)：如果自動載入屬性或非同步服務查詢要求封裝載入，Visual Studio 2015 中的新 AsyncPackage 基類可讓您以非同步方式在背景中載入 Visual Studio 套件。 此背景載入可讓 IDE 保持回應。 即使延伸模組是在背景中初始化，以及啟動和解決方案載入等重要案例中都不會受到影響，IDE 仍會有回應。

[非同步服務](how-to-provide-an-asynchronous-visual-studio-service.md)：透過非同步封裝支援，我們也新增了以非同步方式查詢服務的支援，而且能夠註冊非同步服務。 更重要的是，我們正努力將核心 Visual Studio 服務轉換成支援非同步查詢，讓非同步查詢中的大部分工作都發生在背景執行緒中。 SComponentModel (Visual Studio MEF 主機) 是其中一項主要服務，現在支援非同步查詢，以允許延伸模組完全支援非同步載入。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>減少自動載入擴充功能的影響

如果封裝仍需要在啟動時自動載入，請務必將封裝初始化期間完成的工作降至最低。 將封裝初始化工作降至最低，可減少擴充功能影響啟動的機率。

某些可能會導致封裝初始化成本高昂的範例如下：

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步封裝載入，而不是非同步封裝載入

由於同步封裝預設是在主執行緒上載入，因此我們鼓勵具有自動載入封裝的延伸模組擁有者改用非同步封裝基類，如先前所述。 將自動載入的封裝變更為支援非同步載入也可讓您更輕鬆地解決下列其他問題。

### <a name="synchronous-filenetwork-io-requests"></a>同步檔案/網路 IO 要求

在理想的情況下，您應該避免在主執行緒中進行任何同步檔案或網路 IO 要求。 它們的影響取決於電腦狀態，而且在某些情況下可能會封鎖很長一段時間。

使用非同步封裝載入和非同步 IO Api 應該確保封裝初始化不會在這種情況下封鎖主執行緒。 使用者也可以繼續與 Visual Studio 互動，而 i/o 要求則會在背景中發生。

### <a name="early-initialization-of-services-components"></a>服務、元件的早期初始化

封裝初始化中的其中一個常見模式是初始化服務，或是由封裝或方法中該封裝所提供的 `constructor` 服務 `initialize` 。 雖然這可確保服務已可供使用，但如果未立即使用這些服務，也會將不必要的成本新增至封裝載入。 相反地，這類服務應視需要初始化，以將封裝初始化中完成的工作降至最低。

針對套件所提供的全域服務，您可以使用 `AddService` 方法來延遲只有在元件要求服務時，才會將服務延遲初始化。 針對在封裝內使用的服務，您可以使用消極 \<T> 或改用 asynclazy<t>， \<T> 以確保服務會在第一次使用時初始化/查詢。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>使用活動記錄測量自動載入的擴充功能的影響

從 Visual Studio 2017 Update 3 開始，Visual Studio 活動記錄檔現在會包含在啟動和載入解決方案時，對封裝產生效能影響的專案。 為了查看這些測量，您必須使用/log 參數開啟 Visual Studio，並開啟 *ActivityLog.xml* 檔案。

在活動記錄中，專案會在 [管理 Visual Studio 效能] 來源底下，看起來會像下列範例：

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

此範例顯示在 Visual Studio 啟動時，GUID 為 "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" 的封裝花了2008毫秒。 請注意，當計算封裝的影響時，Visual Studio 會將最上層成本視為主要數位，因為當使用者停用該套件的延伸模組時，就會看到這種情況。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>使用 PerfView 測量自動載入擴充功能的影響

雖然程式碼分析有助於找出可能使封裝初始化變慢的程式碼路徑，您也可以使用 PerfView 之類的應用程式來瞭解封裝載入的影響，以瞭解封裝載入 Visual Studio 啟動的影響。

PerfView 是全系統的追蹤工具。 這項工具可協助您瞭解應用程式中的最忙碌路徑，這是因為 CPU 使用量或封鎖系統呼叫。 以下是使用 [Microsoft 下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=28567)提供的 PerfView 分析範例延伸模組的快速範例。

**範例程式碼：**

此範例是以下列範例程式碼為基礎，其設計目的是要顯示一些常見的延遲原因：

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**使用 PerfView 記錄追蹤：**

設定您的擴充功能並安裝您的 Visual Studio 環境之後，您可以開啟 PerfView，並從 [**收集**] 功能表開啟 [**收集**] 對話方塊，以記錄啟動追蹤。

![perfview 收集功能表](media/perfview-collect-menu.png)

預設選項會提供 CPU 耗用量的呼叫堆疊，但因為我們也對封鎖時間有興趣，所以您也應該啟用 **執行緒時間** 堆疊。 設定就緒之後，您可以按一下 [ **開始收集** ]，然後在錄製開始之後開啟 Visual Studio。

在您停止收集之前，您想要確定 Visual Studio 已完全初始化、主視窗完全可見，而且如果您的延伸模組具有任何自動顯示的 UI 片段，也會顯示它們。 當 Visual Studio 完全載入並初始化您的延伸模組時，您可以停止錄製來分析追蹤。

**使用 PerfView 分析追蹤：**

完成錄製後，PerfView 會自動開啟追蹤和展開選項。

基於此範例的目的，我們會對您在 [ **Advanced Group**] 之下找到的 [**執行緒時間堆疊**] 視圖感興趣。 這個視圖會顯示一個方法花費線上程上的總時間，包括 CPU 時間和封鎖時間，例如磁片 IO 或等候控制碼。

 ![執行緒時間堆疊](media/perfview-thread-time-stacks.png)

 開啟 **執行緒時間堆疊** 視圖時，您應該選擇 **devenv** 進程來開始分析。

PerfView 有詳細的指引，說明如何在其自己的 [說明] 功能表下讀取執行緒時間堆疊，以便進行更詳細的分析。 基於此範例的目的，我們想要進一步篩選此視圖，方法是在套件模組名稱和啟動執行緒中只包含堆疊。

1. 將 **GroupPats** 設定為空白文字，以移除依預設新增的任何群組。
2. 將 **IncPats** 設定為包含部分元件名稱和啟動執行緒，以及現有的進程篩選。 在此情況下，它應該是 **devenv;啟動執行緒;MakeVsSlowExtension**。

現在，此視圖只會顯示與延伸模組相關之元件的相關成本。 在此觀點中，啟動執行緒的 **Inc (內含成本)** 資料行下所列的任何時間，都會與我們篩選的延伸模組相關，並會影響啟動。

在上述範例中，有一些有趣的呼叫堆疊會是：

1. 使用類別的 IO `System.IO` ：雖然這些框架的內含成本在追蹤中可能不太昂貴，但它們是問題的可能原因，因為檔案 IO 速度會因電腦而異。

   ![系統 io 框架](media/perfview-system-io-frames.png)

2. 封鎖呼叫等候其他非同步工作：在此情況下，內含時間代表在非同步工作完成時封鎖主執行緒的時間。

   ![封鎖呼叫框架](media/perfview-blocking-call-frames.png)

追蹤中可用於判斷影響的其他其中一個視圖將會是 **影像載入堆疊**。 您可以套用套用至 **執行緒時間堆疊** 的相同篩選，並找出因為自動載入封裝所執行的程式碼而載入的所有元件。

將封裝初始化常式內載入的元件數目降到最低，因為每個額外的元件都牽涉到額外的磁片 i/o，因此較慢的機器上可能會大幅降低啟動速度。

## <a name="summary"></a>摘要

Visual Studio 的啟動是我們持續收到意見反應的領域之一。 如先前所述，我們的目標是讓所有使用者都擁有一致的啟動體驗，無論其所安裝的元件和延伸模組為何。 我們想要與延伸模組擁有者合作，以協助我們達成此目標。 上述指導方針有助於瞭解延伸模組對啟動的影響，並避免需要以非同步方式自動載入或載入，以將對使用者生產力的影響降到最低。
