---
title: HOW TO：診斷延伸模組效能 |Microsoft Docs
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 2d9337b443fdaabe713f1708b2be9051c2f02b3c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707064"
---
# <a name="measuring-extension-impact-in-startup"></a>測量的延伸模組影響啟動

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>著重在 Visual Studio 2017 中的延伸模組效能

根據客戶意見反應，Visual Studio 2017 版本的焦點區域的其中一個已啟動和方案載入效能。 為 Visual Studio 平台小組中，我們擁有已致力於改善啟動和方案載入效能。 一般情況下，我們測量建議安裝的擴充功能也可以在這些情況下有相當大的影響。

若要協助使用者了解這種影響中,，我們會新增新的功能在 Visual Studio 中，通知使用者緩慢延伸模組。 某些情況下，Visual Studio 會偵測新的延伸模組的解決方案載入或啟動變慢。 偵測到的速度變慢時，使用者會看到通知，以在 IDE 中指向新的 [管理 Visual Studio 效能] 對話方塊。 若要瀏覽先前偵測到的延伸模組的 [說明] 功能表也一律可以存取此對話方塊。

![管理 Visual Studio 效能](media/manage-performance.png)

本文件旨在協助延伸模組開發人員透過描述擴充功能影響的計算方式。 本文件也說明如何在本機分析擴充功能的影響。 在本機分析擴充功能的影響，會決定是否擴充功能可能會顯示為效能影響擴充功能。

> [!NOTE]
> 本文件著重於在啟動和方案載入的擴充功能的影響。 延伸模組也會影響 Visual Studio 效能時，會變得沒有回應 UI。 如需本主題的詳細資訊，請參閱[How to:診斷 UI 延伸模組造成的延遲](how-to-diagnose-ui-delays-caused-by-extensions.md)。

## <a name="how-extensions-can-impact-startup"></a>延伸模組可以列印文件的影響，請啟動

其中一種會影響啟動效能的延伸模組的最常見的方式是藉由選擇要在其中一個已知的啟動 UI 內容，例如 NoSolutionExists 或 ShellInitialized 自動載入。 這些 UI 內容會在啟動時啟動。 包含任何套件`ProvideAutoLoad`屬性在其定義中使用這些內容會載入並在該時間初始化。

當我們量值延伸模組的影響時，我們主要著重在選擇上述的內容中的自動載入這些擴充功能所花費的時間。 測量時間會包含但不是限於：

* 載入的延伸模組組件同步的封裝
* 同步的封裝的封裝類別建構函式所花費的時間
* 在同步的封裝的封裝初始化 （或 SetSite） 方法所花費的時間
* 針對非同步的套件，背景執行緒上執行上述作業。  因此，作業會排除在監視之外。
* 在 排程封裝初始化期間，主執行緒上執行任何非同步工作中所花費的時間
* 在 事件處理常式，尤其是初始化殼層內容啟用或 shell 廢止狀態變更所花費的時間
* 從 Visual Studio 2017 Update 3 開始，我們將也會開始監視所花費的時間在閒置的呼叫之前初始化殼層。 閒置處理常式中的長時間作業也會造成停止回應的 IDE，而提供給使用者感知的啟動時間。

我們新增了從 Visual Studio 2015 的許多功能。 這些功能協助進行而不需要自動載入的封裝。 功能也可以延後封裝以載入更多特定案例的需求。 這些案例包括其中使用者會使用延伸模組，或減少時自動載入的延伸模組影響更特定的範例。

下列文件中，您可以找到有關這些功能的更多詳細資料：

[以規則為基礎的 UI 內容](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md):建置 UI 內容更豐富規則式引擎，可讓您建立根據專案類型、 類別和屬性的自訂內容。 自訂內容可用來在較特定案例期間載入的封裝。 這些特定情況下會包含為特定的功能，而不是啟動專案的目前狀態。 自訂的內容也可讓[命令繫結至自訂內容的可見性](visibilityconstraints-element.md)根據專案元件或其他可用的詞彙。 這項功能就不需要載入的封裝，以註冊命令狀態查詢處理常式。

[非同步的套件支援](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md):Visual Studio 2015 中新的 AsyncPackage 基底類別可讓 Visual Studio 封裝要載入在背景中以非同步方式載入封裝由自動載入屬性或非同步服務查詢。 這個背景載入可讓 IDE 持續回應。 IDE 是回應式，即使延伸模組會在背景中初始化和啟動和解決方案的負載等重大案例不會受到影響。

[非同步服務](how-to-provide-an-asynchronous-visual-studio-service.md):透過非同步的套件支援，我們也新增支援以非同步方式查詢服務，以及能夠註冊非同步的服務。 更重要的，我們正在轉換至支援非同步查詢，使大部分的非同步查詢中的工作，就會發生在背景執行緒中的核心 Visual Studio 服務。 SComponentModel （Visual Studio 的 MEF 主機） 是其中一個主要服務現在支援 允許延伸模組來支援非同步載入完全非同步查詢。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>減少影響自動載入擴充功能

如果封裝仍必須自動載入在啟動時，務必減少套件初始化期間所執行的工作。 最小化封裝初始化工作減少影響啟動的延伸模組的機會。

可能會導致套件初始化昂貴一些範例包括：

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步的封裝負載，而不是非同步的封裝載入

因為同步的封裝會載入在主執行緒上，依預設，我們鼓勵具有自動載入封裝，如先前所述的而是使用非同步封裝基底類別的延伸模組擁有者。 變更自動載入的封裝來支援非同步載入並且更容易解決下列的其他問題。

### <a name="synchronous-filenetwork-io-requests"></a>同步的檔案/網路 IO 要求數目

在理想情況下應該避免任何同步的檔案或網路 IO 要求，主執行緒中。 其影響視機器狀態，而且長一段時間，在某些情況下可以封鎖。

使用非同步的套件載入和非同步 IO Api 應該要確定該套件初始化不會封鎖主執行緒在這種情況下。 使用者也可以繼續在背景中發生的 I/O 要求時，與 Visual Studio 互動。

### <a name="early-initialization-of-services-components"></a>早期的初始設定的服務、 元件

套件初始化中常見的模式來初始化服務所使用，或提供該套件在套件中有`constructor`或`initialize`方法。 雖然這可確保服務可供使用，它也可以將封裝載入如果這些服務不會立即使用的不必要成本。 而是這類服務應該初始化隨選套件初始化完成的工作降到最低。

針對套件所提供的全域服務，您可以使用`AddService`採用延遲初始化的服務，只會由元件在要求時，才函式的方法。 封裝內所使用的服務，您可以使用 「 延遲<T>或 AsyncLazy<T>並確定服務為第一次使用初始化/查詢。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>衡量影響自動載入延伸模組使用活動記錄檔

從 Visual Studio 2017 Update 3 開始，Visual Studio 活動記錄檔現在會包含封裝的效能影響的項目啟動和方案載入期間。 若要查看這些測量結果，您必須使用 /log 參數啟動 Visual Studio，然後開啟*ActivityLog.xml*檔案。

活動記錄檔中的項目將會在 [管理 Visual Studio 效能] 來源之下，並看起來如下列範例所示：

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

這個範例示範具有 GUID"3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c"的封裝花費 2008 毫秒，Visual Studio 的 「 啟動中。 請注意，Visual Studio 時，考慮最上層的成本做為主要號碼計算封裝的影響，因為這是當它們停用該封裝的擴充功能時，請參閱 < 節省使用者。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>衡量影響自動載入使用 PerfView 的延伸模組

雖然程式碼分析可協助您識別可能會降低封裝初始化的程式碼路徑，您也可以利用追蹤使用 PerfView 之類的應用程式，以了解在 Visual Studio 啟動載入封裝的影響。

PerfView 是全系統追蹤工具。 此工具將可協助您了解應用程式因為 CPU 使用量或封鎖系統呼叫中的最忙碌路徑。 以下是簡單的範例分析的範例擴充功能使用 PerfView 網址[Microsoft 下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=28567)。

**範例程式碼：**

此範例中以範例為基礎下面的程式碼，其設計目的是要顯示案例的一些常見延遲原因：

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

一旦您已安裝的擴充功能設定您的 Visual Studio 環境，您可以開啟 PerfView 並開啟記錄啟動追蹤**收集**從對話方塊**收集**功能表。

![perfview 收集功能表](media/perfview-collect-menu.png)

預設選項會提供 CPU 耗用量的呼叫堆疊，但由於我們有興趣使用封鎖的時間，您也應該讓**執行緒時間**堆疊。 設定可以在準備好您可以按一下**開始收集**並啟動 Visual Studio，一旦開始錄製。

停止集合之前，您會想要確定 Visual Studio 已完全初始化，主視窗是完全可見，而且如果您的延伸模組會自動顯示任何 UI 項目，它們也會顯示。 Visual Studio 完全載入，且您的延伸模組會初始化之後, 您可以停止分析追蹤記錄。

**分析使用 PerfView 追蹤：**

完成錄製之後 PerfView 會自動開啟追蹤，並展開選項。

基於此範例的目的，我們有主要興趣**執行緒時間堆疊**檢視，您可以找到**進階群組**。 此檢視會顯示方法，包括 CPU 時間和已封鎖的時間，例如磁碟 IO，或等候控制代碼的執行緒上所花費的時間總計。

 ![執行緒時間堆疊](media/perfview-thread-time-stacks.png)

 在開啟時**執行緒時間堆疊**檢視，您應該選擇**devenv**程序，以開始分析。

PerfView 有詳細的指引如何讀取執行緒在其本身的更詳細的分析的 [說明] 功能表下的時間堆疊。 基於此範例的詳細資訊，我們想要篩選此檢視進一步只包含我們封裝的模組名稱和啟動執行緒的堆疊。

1. 設定**GroupPats**空的文字，若要移除依預設，加入任何群組。
2. 設定**IncPats**來包含部分除了現有的處理序篩選您的組件名稱和執行緒啟動。 在此情況下，它應該是**devenv;啟動執行緒。MakeVsSlowExtension**。

現在檢視只會顯示已與延伸模組相關的組件建立關聯的成本。 在此檢視中，列在任何時候**Inc （內含成本）** 啟動執行緒的資料行與我們篩選的延伸模組和會影響啟動。

上例一些有趣的呼叫堆疊會是：

1. IO 使用`System.IO`類別：雖然這些框架的內含的成本可能不是太高，則表示追蹤中，它們是問題的可能原因，因為檔案 IO 速度而異機器機器也一樣。

   ![系統 io 框架](media/perfview-system-io-frames.png)

2. 封鎖等候其他非同步工作的呼叫：在此情況下，內含時間代表主執行緒遭到封鎖的非同步工作完成時的時間。

   ![封鎖的呼叫框架](media/perfview-blocking-call-frames.png)

其中一個其他檢視中，有助判斷影響追蹤將會**映像載入堆疊**。 您可以套用相同的篩選套用至**執行緒時間堆疊**檢視，並了解所有組件載入，因為您自動載入的封裝所執行的程式碼。

請務必為每個額外的組件會需要額外的磁碟 I/O，這會降低啟動很慢的電腦上，將載入的組件內封裝的初始化常式數目降至最低。

## <a name="summary"></a>總結

啟動 Visual Studio 已我們持續獲得意見反應區域的其中一個。 我們稍早所述的目標是要讓一致啟動，而不論元件與延伸模組安裝體驗的所有使用者。 我們想要使用延伸模組的擁有者，可以幫助他們協助我們達成該目標。 上述的指導方針應該是幫助您了解延伸模組影響啟動，請避免自動載入或載入它以非同步方式對使用者產能的影響降到最低。
