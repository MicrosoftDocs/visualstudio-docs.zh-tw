---
title: "如何： 診斷延伸模組效能 |Microsoft 文件"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: "1"
author: BertanAygun
ms.author: bertaygu
manager: ghogen
ms.openlocfilehash: c2d8b27937be4580da8ff33c5b3c1d57654b4c89
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="measuring-extension-impact-in-startup"></a>測量延伸模組中啟動的影響

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>專注於擴充功能在 Visual Studio 2017 的效能

根據客戶的意見反應，下列其中一個焦點區域，Visual Studio 2017 版本中已啟動及方案負載的效能。 雖然做為 Visual Studio 平台團隊，我們已使用在一般情況下改善啟動和方案負載的效能，我們遙測建議安裝的擴充功能上的情況下也可以有相當大的影響。

若要協助使用者了解這種影響，我們會通知使用者緩慢的擴充功能的 Visual Studio 中加入的新功能。 當 Visual Studio 偵測到減緩載入方案或啟動新的延伸模組時，則使用者會看到通知，以指向新的 [管理 Visual Studio 效能] 對話方塊在 IDE 中。 若要瀏覽先前偵測到的擴充功能的 [說明] 功能表也永遠可以存取此對話方塊。

![管理 Visual Studio 效能](media/manage-performance.png)

本文旨在協助擴充功能開發人員透過描述擴充功能影響計算的方式以及它可以分析方式在本機以測試擴充功能可能會顯示為效能，從而影響擴充功能。

## <a name="how-extensions-can-impact-startup"></a>擴充功能可能會如何影響啟動

其中一種會影響啟動效能的擴充功能的最常見的方式是藉由選擇要在其中一個已知的啟動 UI 內容，例如 NoSolutionExists 或 ShellInitialized 自動載入。 這些 UI 內容會啟動，並在啟動期間，任何與這些內容其定義中包含"ProvideAutoLoad"屬性的封裝會載入並在該時間初始化。

當我們測量擴充功能的影響時，我們主要著重在上面的內容中的自動載入選擇這些擴充功能所花費的時間。 測量時間會包括但不是限於：

* 載入的延伸模組組件的同步的封裝
* 在同步的套件的套件類別建構函式所花費的時間
* 在同步的封裝的封裝初始化 （或 SetSite） 方法所花費的時間
* 非同步封裝上述的作業在背景執行緒上執行，因此會排除在監視之外
* 在任何排程封裝初始化期間，在主執行緒上執行的非同步工作中所花費的時間
* 在事件處理常式，特別是殼層初始化內容啟動或殼層廢止狀態變更所花費的時間
* 從 Visual Studio 2017 Update 3 開始，我們也會啟動監視殼層初始化之前，花在閒置的呼叫上的時間。 在閒置的處理常式中的長時間作業也會導致沒有回應的 IDE，並加入使用者所見的啟動時間。

我們新增了多個啟動 Visual Studio 2015，若要協助移除封裝到自動負載的需要，延後其載入至更特定情況下，使用者就會使用延伸模組，或載入時，減少延伸影響更特定的功能自動的。

下列文件中，您可以找到更多有關這些功能的詳細資料：

[規則基礎 UI 內容](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)： 更豐富的基礎的規則引擎，建置 UI 內容可讓您建立根據專案類型、 類別和功能的自訂內容。 這些自訂內容可以用來更特定的案例，例如出現在專案中使用的特定功能，而不是啟動; 期間載入的封裝允許或[命令繫結至自訂內容的可見性](visibilityconstraints-element.md)根據專案功能或其他可用的詞彙，因此不需要載入封裝，以註冊命令狀態查詢處理常式。

[非同步封裝支援](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Visual Studio 2015 中新的 AsyncPackage 基底類別可讓 Visual Studio 封裝載入至在背景中以非同步方式如果載入封裝所要求的自動載入屬性或非同步服務查詢. 此背景載入可讓 IDE 擴充功能會在背景中初始化和啟動和方案負載等重大案例不會受到影響時持續回應。

[非同步服務](how-to-provide-an-asynchronous-visual-studio-service.md)： 非同步封裝的支援，我們現在還支援以非同步方式查詢服務，且能以註冊非同步服務。 更重要的，我們正在轉換至支援非同步查詢，因此大部分的非同步查詢中的工作，就會發生在背景執行緒中的核心 Visual Studio 服務。 SComponentModel （Visual Studio MEF 主機） 是其中一個主要服務現在支援 允許延伸模組來支援非同步載入完全非同步查詢。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>減少影響自動載入擴充功能

如果封裝仍必須在啟動時載入的自動，務必影響啟動的擴充功能的機會降低封裝初始化期間完成的工作降至最低。

可能會造成封裝的初始化可能高度耗費資源的部分範例如下：

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步的封裝負載，而不是非同步的封裝載入

因為同步的封裝會載入主執行緒上，依預設，我們鼓勵具有自動載入封裝，如先前所述的而是使用非同步封裝基底類別的延伸模組擁有者。 變更以支援非同步載入自動載入的封裝並且更容易解決下列的其他問題。

### <a name="synchronous-filenetwork-io-requests"></a>同步的檔案/網路 IO 要求

在理想情況下任何同步的檔案或網路 IO 要求您應該避免使用主執行緒中其影響視機器狀態，而且可能會封鎖長的時間，在某些情況下。

使用非同步的封裝載入及應用程式開發介面非同步 IO 應該確保封裝初始化不會封鎖主執行緒在這種情況下，使用者可以繼續在背景中發生的 I/O 要求時，Visual Studio 中的互動。

### <a name="early-initialization-of-services-components"></a>早期的服務元件初始化

初始化封裝中常見的模式之一是初始化服務所使用，或該套件的套件建構函式或初始化方法中所提供。 雖然這可確保服務可供使用，它也可以將封裝載入如果這些服務不會立即使用不必要的成本。 而這類服務應該初始化隨在套件的初始設定中完成的工作減至。

封裝所提供的全域服務，您可以使用接受要求的元件時，才執行延遲初始化服務函式的 AddService 方法。 為了在封裝中使用的服務，您可以利用 Lazy<T>或 AsyncLazy<T>來確認服務已初始化/上接受查詢第一次使用。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>測量影響自動載入延伸模組使用活動記錄檔

從 Visual Studio 2017 Update 3 開始，Visual Studio 活動記錄檔現在會包含封裝的效能影響的項目啟動及方案載入期間。 若要查看這些度量，您必須使用 /log 參數啟動 Visual Studio 開啟 ActivityLog.xml 檔案。

活動記錄檔中的項目將會顯示在 「 管理 Visual Studio 效能 」 來源和看起來類似下列：

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

這表示該封裝具有 GUID"3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c"花費 2008 毫秒中啟動 Visual studio。 請注意，Visual Studio 會考慮 top 層級的成本做為主要號碼計算封裝的影響，因為這是 savigs 使用者時，請參閱這些停用該套件的擴充功能。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>測量影響自動載入使用 PerfView 的擴充功能

雖然程式碼分析可協助您識別封裝初始化速度變慢的程式碼路徑，您也可以利用追蹤使用 PerfView 這類應用程式，以了解在 Visual Studio 啟動時載入封裝的影響。

PerfView 是系統寬追蹤工具，可協助您了解因 CPU 使用量或封鎖系統呼叫的應用程式中的最忙碌路徑。 以下是簡單的範例，可分析的範例延伸模組使用 PerfView 位於[Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567)。

**範例程式碼：**

這個範例根據範例下列程式碼，其設計目的是要顯示的大小寫一些常見的延遲的原因：

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

**記錄使用 PerfView 追蹤：**

一旦您安裝 Visual Studio 環境與您安裝的擴充功能，您可以藉由開啟 PerfView，並從"收集"功能表開啟收集的對話方塊記錄啟動追蹤。

![perfview 收集功能表](media/perfview-collect-menu.png)

預設的選項將會提供 CPU 耗用率的呼叫堆疊，但由於我們有興趣中封鎖的時間，您也應該讓 「 執行緒的時間 」 堆疊。 設定可以在準備好您可以按一下 「 啟動集合 」，然後啟動 Visual Studio，一旦開始錄製。

停止收集之前，您會想要確定 Visual Studio 已完全初始化，主視窗是完全可見的如果您的擴充功能會自動顯示任何 UI 項目，它們也是可見。 當 Visual Studio 是完全載入，而且會初始化您的擴充功能時，您可以停止記錄來分析追蹤。

**分析使用 PerfView 追蹤：**

完成錄製 PerfView 會自動開啟追蹤，並展開選項。

基於此範例的目的，我們感主要中的 「 進階群組 」 下找到"執行緒時間堆疊 」 檢視。 此檢視會顯示方法，包括 CPU 時間和封鎖的時間，例如磁碟 IO，或等候控制代碼的執行緒上花費時間總計。

 ![執行緒的時間堆疊](media/perfview-thread-time-stacks.png)

 當開啟 「 執行緒時間堆疊 」 檢視，您應該選擇"devenv 」 程序開始分析。

PerfView 詳述如何讀取執行緒在其本身的更詳細的分析的 [說明] 功能表下的時間堆疊的指引。 基於此範例中，我們想要篩選這個檢視進一步只包括與我們封裝模組名稱和啟動執行緒的堆疊。

1. "GroupPats"設為空的文字，若要移除依預設，加入任何群組。
2. 除了現有的處理序篩選的集合 」 IncPats 」 包含組件名稱的一部分，而且啟動執行緒。 在此情況下，它應該是"devenv;啟動執行緒。MakeVsSlowExtension"。

現在檢視只會顯示與副檔名相關的組件的相關成本。 在此檢視中啟動執行緒的"Inc"（內含成本） 資料行底下所列的任何時間是篩選擴充功能和相關影響啟動。

一些有趣的呼叫上述範例會是堆疊：

1. IO 使用 System.IO 類別： 內含成本這些框架可能不是非常耗費資源，則表示追蹤中，很可能的原因是發生問題由於檔案 IO 的速度將不同的電腦。

  ![系統 io 框架](media/perfview-system-io-frames.png)

2. 封鎖呼叫的其他非同步工作在等候： 在此情況下內含時間代表主執行緒會封鎖的非同步工作完成的時間。

  ![封鎖呼叫框架](media/perfview-blocking-call-frames.png)

其中一個其他檢視將有助於判斷影響在追蹤中會 「 映像載入堆疊 」。 您可以套用相同的篩選套用至 「 執行緒時間堆疊 」 檢視，並找出所有組件載入，因為您的自動載入封裝所執行的程式碼。

請務必載入的組件內封裝的初始化常式數目降至最低，每個額外的組件會涉及額外的磁碟 I/O 大幅變慢的電腦上的啟動速度變慢。

## <a name="summary"></a>總結

啟動 Visual Studio 已我們持續取得回應的區域。 我們稍早所述的目標是要讓所有使用者有一致的啟動不論元件和副檔名，則安裝體驗，我們想要使用延伸模組的擁有者可以幫助他們幫助我們實現此目標。 上述指引應有助於了解啟動影響到擴充功能和可以避免需要自動載入或載入它以非同步方式對使用者產能的影響降到最低。
