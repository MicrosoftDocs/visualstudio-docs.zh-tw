---
title: 如何：診斷擴充功能效能 |Microsoft Docs
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 542d8a6d6d90091aa7a800ef18f847fea6b1a81c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905913"
---
# <a name="measuring-extension-impact-in-startup"></a>測量擴充功能在啟動時的影響

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>專注于 Visual Studio 2017 中的延伸模組效能

根據客戶的意見反應，Visual Studio 2017 版本的其中一個焦點區域是啟動和解決方案載入效能。 身為 Visual Studio 平臺小組，我們一直致力於改善啟動和解決方案載入效能。 一般而言，我們的度量建議已安裝的延伸模組也會對這些案例造成相當大的影響。

為了協助使用者瞭解這種影響，我們在 Visual Studio 中新增了一項新功能，以通知使用者使用緩慢的延伸模組。 有時候，Visual Studio 會偵測到新的擴充功能，而使解決方案載入或啟動變慢。 偵測到緩慢時，使用者會在 IDE 中看到通知，指向新的 [管理 Visual Studio 效能] 對話方塊。 [說明] 功能表也可以隨時存取此對話方塊，以流覽先前偵測到的延伸模組。

![管理 Visual Studio 效能](media/manage-performance.png)

本檔旨在說明延伸模組影響的計算方式，藉此協助擴充開發人員。 本檔也會說明如何在本機分析延伸模組的影響。 在本機分析延伸模組影響將會判斷延伸模組是否可能顯示為影響效能的延伸模組。

> [!NOTE]
> 本檔著重于延伸模組在啟動和解決方案載入方面的影響。 延伸模組也會在導致 UI 變得沒有回應時，影響 Visual Studio 效能。 如需本主題的詳細資訊，請參閱[如何：診斷擴充功能所造成的 UI 延遲](how-to-diagnose-ui-delays-caused-by-extensions.md)。

## <a name="how-extensions-can-impact-startup"></a>延伸模組可能影響啟動的方式

影響啟動效能的擴充功能最常見的一種方式，是選擇自動載入其中一個已知的啟動 UI 內容，例如 NoSolutionExists 或 ShellInitialized。 這些 UI 內容會在啟動期間啟用。 在這些內容的定義中包含屬性的任何封裝 `ProvideAutoLoad` ，將會在該時間載入並初始化。

當我們測量擴充功能的影響時，主要著重于這些延伸模組所花費的時間，這些擴充功能會選擇在上述內容中自動載入。 測量的時間包括但不限於：

* 載入同步封裝的擴充元件
* 針對同步封裝在封裝類別的函式中花費的時間
* 同步封裝的封裝初始化（或 SetSite）方法所花費的時間
* 針對非同步封裝，上述作業會在背景執行緒上執行。  因此，作業會從監視中排除。
* 在封裝初始化期間排程于主執行緒上執行的任何非同步工作所花費的時間
* 事件處理常式中花費的時間，特別是 shell 初始化內容啟用或 shell 廢止狀態變更
* 從 Visual Studio 2017 Update 3 開始，我們也會在初始化 shell 之前，開始監視閒置呼叫所花費的時間。 閒置處理常式中的長時間作業也會造成沒有回應的 IDE，並由使用者參與察覺的啟動時間。

我們新增了許多功能，從 Visual Studio 2015 開始。 這些功能可協助您移除封裝自動載入的需求。 這些功能也會延遲封裝載入更特定案例的需求。 這些情況包括使用者在自動載入時，使用延伸模組或減少擴充功能影響的範例。

您可以在下列檔中找到更多有關這些功能的詳細資料：

以[規則為基礎的 ui](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)內容：以 ui 內容為基礎的更豐富規則型引擎，可讓您根據專案類型、類別和屬性來建立自訂內容。 自訂內容可以在更特定的案例中用來載入封裝。 這些特定案例包括具有特定功能的專案是否存在，而不是啟動。 自訂內容也允許根據專案元件或其他可用詞彙，[將命令可見度系結至自訂內容](visibilityconstraints-element.md)。 這項功能不需要載入封裝來註冊命令狀態查詢處理常式。

[非同步封裝支援](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)：如果自動載入屬性或非同步服務查詢要求封裝載入，則 Visual Studio 2015 中的新 AsyncPackage 基類可讓 Visual Studio 封裝以非同步方式載入到背景中。 此背景載入可讓 IDE 保持回應。 即使在背景中初始化延伸模組，以及啟動和解決方案載入之類的重大案例中，IDE 仍會有回應，因此不會受到影響。

[非同步服務](how-to-provide-an-asynchronous-visual-studio-service.md)：有了非同步封裝支援，我們也新增了以非同步方式查詢服務，以及能夠註冊非同步服務的支援。 更重要的是，我們正努力將核心 Visual Studio 服務轉換成支援非同步查詢，以便非同步查詢中的大部分工作都是在背景執行緒中執行。 SComponentModel （Visual Studio MEF 主機）是目前支援非同步查詢的其中一項主要服務，可讓延伸模組完全支援非同步載入。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>減少自動載入擴充功能的影響

如果封裝仍然需要在啟動時自動載入，請務必將封裝初始化期間所完成的工作降到最低。 最小化套件初始化工作可減少擴充功能影響啟動的機率。

可能導致封裝初始化成本高昂的部分範例如下：

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>使用同步封裝載入，而不是非同步封裝載入

由於預設會在主執行緒上載入同步封裝，因此我們鼓勵具有自動載入封裝的延伸模組擁有者，改為使用非同步封裝基類，如先前所述。 變更自動載入的封裝以支援非同步載入，也能讓您更輕鬆地解決下列其他問題。

### <a name="synchronous-filenetwork-io-requests"></a>同步檔案/網路 IO 要求數

在理想情況下，應該避免在主執行緒中進行任何同步檔案或網路 IO 要求。 其影響會視機器狀態而定，而且在某些情況下可能會長時間封鎖。

使用非同步封裝載入和非同步 IO Api 時，應該確保封裝初始化不會在這類情況下封鎖主執行緒。 使用者也可以繼續與 Visual Studio 互動，而 i/o 要求會在背景中發生。

### <a name="early-initialization-of-services-components"></a>早期初始化服務、元件

封裝初始化中的其中一個常見模式是將使用的服務初始化，或由封裝或方法中的該封裝所提供 `constructor` `initialize` 。 雖然這可確保服務可供使用，但如果未立即使用這些服務，也會在封裝載入時增加不必要的成本。 相反地，這類服務應視需要初始化，以將在封裝初始化中完成的工作減至最少。

針對封裝所提供的全域服務，您可以使用 `AddService` 方法，只在元件要求服務時，才會將它延遲初始化。 針對封裝內使用的服務，您可以使用 Lazy \<T> 或 asynclazy<t> \<T> 來確保服務會在第一次使用時初始化/查詢。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>使用活動記錄測量自動載入擴充功能的影響

從 Visual Studio 2017 Update 3 開始，Visual Studio 活動記錄檔現在會包含在啟動和解決方案載入期間，封裝對效能影響的專案。 若要查看這些測量，您必須開啟具有/log 參數的 Visual Studio，然後開啟*ActivityLog.xml*檔案。

在 [活動記錄檔] 中，專案會在 [管理 Visual Studio 效能] 來源底下，看起來如下列範例所示：

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

這個範例顯示，GUID 為 "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" 的封裝在 Visual Studio 啟動時花費了2008毫秒。 請注意，在計算套件的影響時，Visual Studio 會將最上層成本視為主要數位，這會是使用者停用該套件的延伸模組時所看到的節約。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>使用 PerfView 測量自動載入擴充功能的影響

雖然程式碼分析有助於識別可能會使套件初始化變慢的程式碼路徑，但您也可以使用 PerfView 之類的應用程式來使用追蹤，以瞭解封裝負載在 Visual Studio 啟動中的影響。

PerfView 是全系統的追蹤工具。 這項工具可協助您瞭解應用程式中的最忙碌路徑，原因可能是 CPU 使用量或封鎖系統呼叫。 以下是使用 PerfView （可從[Microsoft 下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=28567)取得）分析範例延伸模組的快速範例。

**範例程式碼：**

這個範例是以下列範例程式碼為基礎，其設計目的是要顯示一些常見的延遲原因：

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

一旦您設定了已安裝延伸模組的 Visual Studio 環境之後，就可以開啟 PerfView，並從 [**收集**] 功能表開啟 [**收集**] 對話方塊，以記錄啟動的追蹤。

![perfview 收集功能表](media/perfview-collect-menu.png)

預設選項會提供 CPU 耗用量的呼叫堆疊，但由於我們也對封鎖時間有興趣，您也應該啟用**執行緒時間**堆疊。 設定就緒之後，您可以按一下 [**開始收集**]，然後在錄製開始後開啟 Visual Studio。

在您停止收集之前，您想要確定 Visual Studio 已完全初始化，主視窗完全可見，如果您的擴充功能有任何自動顯示的 UI 部分，則也會顯示。 當 Visual Studio 完全載入，且您的擴充功能已初始化時，您可以停止記錄來分析追蹤。

**使用 PerfView 分析追蹤：**

錄製完成後，PerfView 會自動開啟追蹤並展開選項。

基於此範例的目的，我們主要對 [**執行緒時間堆疊**] 視圖感興趣，您可以在 [ **Advanced Group**] 下找到它。 此視圖會以包含 CPU 時間和封鎖時間的方法（例如，磁片 IO 或等待控制碼），顯示執行緒花費的總時間。

 ![執行緒時間堆疊](media/perfview-thread-time-stacks.png)

 開啟**執行緒時間堆疊**視圖時，您應該選擇**devenv**進程以開始分析。

PerfView 有詳細的指引，說明如何在自己的 [說明] 功能表下讀取執行緒時間堆疊，以進行更詳細的分析。 基於此範例的目的，我們想要進一步篩選此視圖，只包含包含套件模組名稱和啟動執行緒的堆疊。

1. 將 [ **GroupPats** ] 設定為 [空的文字]，以移除預設新增的任何群組。
2. 將**IncPats**設定為包含元件名稱和啟動執行緒的一部分，以及現有的進程篩選。 在此情況下，它應該是**devenv;啟動執行緒;MakeVsSlowExtension**。

現在，此視圖只會顯示與延伸模組相關之元件相關聯的成本。 在此視圖中，啟動執行緒的 [ **inc. （內含成本）** ] 資料行底下列出的任何時間，都與我們篩選的延伸模組相關，而且會影響啟動。

在上述範例中，有些有趣的呼叫堆疊會是：

1. 使用類別的 IO `System.IO` ：雖然這些框架的內含成本在追蹤中可能不會耗用太多資源，但它們可能是問題的原因，因為檔案 IO 速度會因電腦而異。

   ![系統 io 畫面格](media/perfview-system-io-frames.png)

2. 封鎖呼叫等待其他非同步工作：在此情況下，內含時間會代表在非同步工作完成時封鎖主執行緒的時間。

   ![封鎖呼叫框架](media/perfview-blocking-call-frames.png)

追蹤中可用於判斷影響的其他其中一個視圖會是**影像載入堆疊**。 您可以將相同的篩選套用至 [**執行緒時間堆疊**] 視圖，並找出因為自動載入的封裝所執行的程式碼而載入的所有元件。

請務必將套件初始化常式內載入的元件數目降至最低，因為每個額外的元件都需要額外的磁片 i/o，這可能會在較慢的機器上大幅降低啟動速度。

## <a name="summary"></a>摘要

Visual Studio 的啟動是我們持續獲得意見反應的其中一個領域。 如先前所述，我們的目標是讓所有使用者都能擁有一致的啟動體驗，而不論其所安裝的元件和延伸模組為何。 我們想要與延伸模組擁有者合作，協助他們協助我們達成該目標。 上述指導方針有助於瞭解擴充功能對啟動的影響，並避免需要以非同步方式自動載入或載入，以將對使用者生產力的影響降至最低。
