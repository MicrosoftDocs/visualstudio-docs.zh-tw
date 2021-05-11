---
title: 程式碼剖析工具入門
description: 查看 Visual Studio 中可用的各種診斷工具。
ms.custom: ''
ms.date: 02/18/2021
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5fb35c1cd30f872d2a58504f73596357cc60025
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729321"
---
# <a name="first-look-at-profiling-tools"></a>初步認識分析工具

Visual Studio 提供各種不同的分析工具，可協助您依據應用程式類型來診斷不同類型的效能問題。 在本文中，我們將快速瞭解最常見的程式碼剖析工具。

若要查看不同應用程式類型的程式碼剖析工具支援，請參閱 [應該使用哪一種工具？](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>在進行調試時測量效能

您可以在偵錯工作階段期間，存取 [診斷工具] 視窗提供的分析工具。 [診斷工具] 視窗會自動出現，除非您將其關閉。 若要顯示視窗，請按一下 [ **Debug/Windows/Show 診斷工具**] (或按 **Ctrl**  +  **Alt**  +  **F2**) 。 視窗開啟時，您可以選取要用來收集資料的工具。

![診斷工具視窗](../profiling/media/prof-tour-diagnostic-tools.png "診斷工具")

在進行偵錯期間，您可以使用 [診斷工具] 視窗，分析 CPU 和記憶體使用量，您也可以檢視顯示效能相關資訊的事件。

![診斷工具摘要視圖](../profiling/media/prof-tour-cpu-and-memory-graph.gif "診斷工具摘要")

**診斷工具** 視窗是分析應用程式的常見方式，但針對發行組建，您也可以改為對應用程式進行事後剖析後的分析。 如需不同方法的詳細資訊，請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 若要查看不同應用程式類型的程式碼剖析工具支援，請參閱 [應該使用哪一種工具？](#which-tool-should-i-use)

診斷工具視窗或在調試過程中提供的工具組括：
- [CPU 使用量](../profiling/beginners-guide-to-performance-profiling.md)
- [記憶體使用量](../profiling/memory-usage.md)
- [效能提示](../profiling/perftips.md)

> [!NOTE]
> Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具] 視窗)。 您可以搭配 Windows 7 及更新版本使用 [事後剖析後](#post_mortem) 工具。 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> 測量發行組建中的效能

效能分析工具中的工具旨在提供 **發行** 組建的分析。 在效能分析工具中，您可以在應用程式執行時收集診斷資訊，然後在應用程式停止 (事後剖析後分析) 之後，檢查所收集的資訊。

選擇 **Debug**  >  **效能分析工具** (或 **Alt + F2**) 以開啟效能分析工具。

![效能分析工具](../profiling/media/prof-tour-performance-profiler.png "效能分析工具")

如需有關使用 [CPU 使用量] 或 [記憶體使用量] 工具的詳細資訊效能分析工具與偵錯工具整合的工具，請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 

效能分析工具中提供的工具組括：

- [CPU 使用量](../profiling/cpu-usage.md)
- [.NET 物件配置](../profiling/dotnet-alloc-tool.md)
- [記憶體使用量](../profiling/memory-usage-without-debugging2.md)
- [.NET async 工具](../profiling/analyze-async.md)
- [資料庫工具](../profiling/analyze-database.md)
- [GPU 使用量](../profiling/gpu-usage.md)

若要查看不同應用程式類型的程式碼剖析工具支援，請參閱 [應該使用哪一種工具？](#which-tool-should-i-use)

在某些情況下，視窗可讓您選取 [多個程式碼剖析工具](../profiling/use-multiple-profiler-tools-simultaneously.md)。 [CPU 使用量] 這類工具也可以提供有助於分析的補充資料。 您也可以使用 [命令列](../profiling/profile-apps-from-command-line.md) 分析工具來啟用牽涉到多個程式碼剖析工具的情節。

## <a name="examine-performance-using-perftips"></a>使用效能提示檢查效能

通常，最簡單的方式是使用 [效能提示](../profiling/perftips.md)來查看效能資訊。 您可以使用效能提示，在與程式碼互動時查看效能資訊。 您可以檢查事件持續時間等資訊 (從上次暫停偵錯工具或應用程式啟動時開始測量)。 例如，如果您逐步執行程式碼 (F10，F11) ，效能提示會向您顯示上一個步驟作業到目前步驟的應用程式執行時間持續時間。

![分析導覽效能提示](../profiling/media/prof-tour-perf-tips.png "分析導覽效能提示")

您可以使用效能提示來檢查程式碼區塊執行所需的時間，或是單一函式完成所需的時間。

效能提示顯示的事件也會顯示在診斷工具的 [ **事件** ] 視圖中。 在 [ **事件** ] 視圖中，您可以查看正在進行偵錯工具時所發生的不同事件，例如中斷點或程式碼逐步執行作業的設定。

![診斷工具事件檢視](../profiling/media/prof-tour-events.png "診斷工具 View 事件")

 > [!NOTE]
 > 如果您有 Visual Studio Enterprise，也可以查看這個索引標籤中的 [IntelliTrace 事件](../debugger/intellitrace.md)。

## <a name="analyze-cpu-usage"></a>分析 CPU 使用量

CPU 使用量工具是您開始分析應用程式效能的最佳入門。 它會告訴您應用程式耗用的 CPU 資源詳細資訊。 您可以使用 [偵錯工具整合的 Cpu 使用量工具](../profiling/beginners-guide-to-performance-profiling.md) 或 [事後剖析後的 cpu 使用量工具](../profiling/cpu-usage.md)。

使用偵錯工具整合的 [CPU 使用量] 工具時，開啟 [診斷工具] 視窗 (如果已關閉，請選擇 [ **Debug/Windows/Show] 診斷工具**) 。 在進行調試時，開啟  **摘要** 視圖，然後選取 [ **記錄 CPU 設定檔**]。

![啟用診斷工具中的 CPU 使用量](../profiling/media/prof-tour-enable-cpu-profiling.png "診斷工具啟用 CPU 使用量")

使用此工具的其中一種方式，是在您的程式碼中設定兩個中斷點，一個是在函式的結尾，另一個則是您想要分析的程式碼區域。 當您在第二個中斷點上暫停時，即可檢查分析資料。

[CPU 使用量] 檢視會顯示一份執行時間最長的函式清單，並將時間最長的放在頂端來排序。 這可協助引導您找出發生效能瓶頸的函式。

![診斷工具 CPU 使用量視圖](../profiling/media/prof-tour-cpu-usage.png "診斷工具 CPU 使用量")

按兩下要查看的函式，即會看到更詳細的三個窗格「蝶型」檢視：視窗中間為已選取的函式、左側為發出呼叫的函式，右側為接收呼叫的函式。 [函式主體] 區段會顯示函式主體所花費的總時間 (和時間百分比)，但不包括發出呼叫的函式和接收呼叫的函式所花的時間。 這項資料可協助您評估函式本身是否有效能瓶頸。

![診斷工具呼叫端「蝴蝶」視圖](../profiling/media/prof-tour-cpu-usage-caller-callee.png "診斷工具呼叫端的被呼叫端視圖")

## <a name="analyze-memory-usage"></a>分析記憶體使用量

**診斷工具**] 視窗也可讓您使用 [**記憶體使用量**] 工具來評估應用程式中的記憶體使用量。 例如，您可以查看堆積的物件數目和大小。 您可以使用 [偵錯工具整合的記憶體使用量工具](../profiling/memory-usage.md) 或效能分析工具中的 [事後剖析後記憶體使用量](../profiling/memory-usage-without-debugging2.md) 工具。

.NET 開發人員可以選擇 [.Net 物件組態工具](../profiling/dotnet-alloc-tool.md) 或 [ [記憶體使用量](../profiling/memory-usage.md) ] 工具。

- **.Net 物件配置** 工具可協助您識別 .net 程式碼中的配置模式和異常，並協助找出垃圾收集的常見問題。 此工具只會以事後剖析後工具的形式執行。 您可以在本機或遠端電腦上執行此工具。
- **記憶體使用量** 工具很適合用來識別記憶體流失，通常在 .net 應用程式中並不常見。 如果您在檢查記憶體時需要使用偵錯工具功能，例如逐步執行程式碼，則建議使用 [偵錯工具整合的記憶體使用量](../profiling/beginners-guide-to-performance-profiling.md) 工具。

若要使用 [ **記憶體使用量** ] 工具來分析記憶體使用量，您需要至少取得一個記憶體快照集。 通常，分析記憶體的最佳方式是擷取兩個快照：第一個快照是在可能發生記憶體問題之前擷取，第二個快照則是緊接在可能發生記憶體問題之後擷取。 然後您可以檢視兩個快照的差異，並查看其中到底有什麼變更。 下圖顯示如何使用偵錯工具整合的工具來製作快照集。

![取得診斷工具中的快照集](../profiling/media/prof-tour-take-snapshots.gif "診斷工具拍攝快照集")

當您選取其中一個箭號連結時，您會看到堆積的差異視圖 (紅色向上箭號 ![記憶體使用量增加](../profiling/media/prof-tour-mem-usage-up-arrow.png "記憶體使用量增加") 會顯示遞增的物件計數 (左) 或增加的堆積大小 (右邊) ) 。 如果您按一下右邊的連結，即會取得差異堆積檢視，該檢視會以堆積大小增加最多的物件來排序。 這麼做有助您鎖定記憶體的問題。 如下圖所示，`ClassHandlersStore` 物件使用的位元組在第二張快照中增加了 3,492 個位元組。

![診斷工具堆積差異視圖](../profiling/media/prof-tour-mem-usage-diff-heap.png "診斷工具堆積差異視圖")

如果您按一下左側的連結，而不是 [記憶體使用量] 檢視，堆積檢視就會依照物件計數來組織；數目增加最多的特定類型物件會顯示在頂端 (依 [計數差異] 資料行排序)。

## <a name="analyze-resource-consumption-xaml"></a>分析資源取用量 (XAML)

在 XAML 應用程式 (例如 Windows 傳統型 WPF 應用程式和 UWP App) 中，您可以使用應用程式時間軸工具來分析資源耗用量。 例如，您可以分析應用程式準備 UI 畫面格 (版面配置和轉譯)、服務網路和磁碟要求，以及像是應用程式啟動、頁面載入和視窗大小調整等情況所花費的時間。 若要使用此工具，請選擇 [效能分析工具] 中的 [應用程式時間軸]，然後選擇 [開始]。 在應用程式中，完整瀏覽具有可疑資源消耗問題的案例，然後選擇 [停止收集] 以產生報表。

如果您執行應用程式時出現視覺化的問題，其可能反應在 [視覺輸送量] 圖形中的低畫面播放速率。 同樣地，若出現 UI 回應性問題，也可能會反應在 [UI 執行緒使用率] 圖形中居高的數字。 您可以在報表中針對可疑的效能問題選擇一個時段，然後檢查 [時間軸] 詳細資料檢視 (下方窗格) 中的詳細 UI 執行緒活動。

![應用程式時間軸程式碼剖析工具](../profiling/media/prof-tour-application-timeline.gif "分析導覽應用程式時間軸")

在時間軸詳細資料檢視中，您可以找到相關資訊，例如活動的類型 (或相關的 UI 元素) 以及活動的持續時間。 例如，圖例中，格線控制項的 [配置] 事件花了 57.53 毫秒。

如需詳細資訊，請參閱[應用程式時間軸](../profiling/application-timeline.md)。

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>檢查應用程式事件

一般 [事件檢視器](../profiling/events-viewer.md) 可讓您透過事件清單（例如模組載入、執行緒啟動和系統設定）來查看應用程式的活動，以協助更妥善地診斷您的應用程式在 Visual Studio profiler 內的執行狀況。 這項工具可在效能分析工具中取得。 選擇 **Debug**  >  **效能分析工具** (或 **Alt + F2**) 以開啟效能分析工具。

此工具會在清單視圖中顯示每個事件。 資料行提供每個事件的相關資訊，例如事件名稱、時間戳記和處理序識別碼。

![事件檢視器追蹤](../profiling/media/eventviewertrace.png "事件檢視器追蹤")

## <a name="analyze-asynchronous-code-net"></a> ( .NET) 分析非同步程式碼

[.NET Async 工具](../profiling/analyze-async.md)可讓您分析應用程式中非同步程式碼的效能。 這項工具可在效能分析工具中取得。 選擇 **Debug**  >  **效能分析工具** (或 **Alt + F2**) 以開啟效能分析工具。

此工具會在清單視圖中顯示每個非同步作業。 您可以查看資料的相關資訊，例如開始時間、結束時間和非同步作業的總時間。

![.NET Async 工具已停止](../profiling/media/async-tool-opened.png ".NET Async 工具已停止")

## <a name="analyze-database-performance-net-core"></a> ( .NET Core) 分析資料庫效能

針對使用 ADO.NET 或 Entity Framework Core 的 .NET Core 應用程式， [資料庫工具](../profiling/analyze-database.md) 可讓您在診斷會話期間記錄應用程式所進行的資料庫查詢。 然後，您可以分析個別查詢的相關資訊，以找出可改善應用程式效能的位置。 這項工具可在效能分析工具中取得。 選擇 **Debug**  >  **效能分析工具** (或 **Alt + F2**) 以開啟效能分析工具。

此工具會在清單視圖中顯示每個查詢。 您可以查看查詢開始時間和持續時間等資訊。

![分配](./media/db-gotosource.png "配置")

## <a name="visualize-net-counters-net-core"></a>視覺化 ( .NET Core) 的 .NET 計數器

從 Visual Studio 2019 版本16.7 開始，您可以使用 Visual Studio 中的 [.Net 計數器工具](../profiling/dotnet-counters-tool.md) 將效能計數器視覺化。 您可以使用 [dotnet 計數器](/dotnet/core/diagnostics/dotnet-counters)來視覺化建立的計數器。 dotnet 計數器支援許多計數器，例如 CPU 使用量和垃圾收集行程堆積大小。

此工具會在清單視圖中顯示每個計數器的即時值。

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET 計數器工具收集。":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>檢查 UI 效能和協助工具事件 (UWP)

在 UWP 應用程式中，您可以在 **診斷工具** 視窗中啟用 **UI 分析**。 此工具會搜尋常見的效能或協助工具問題，並於偵錯時將問題顯示在 [事件] 檢視中。 事件描述提供有助您解決問題的相關資訊。

![在診斷工具中查看 UI 分析事件](../profiling/media/prof-tour-ui-analysis.png "診斷工具視圖 UI 分析事件")

## <a name="analyze-gpu-usage-direct3d"></a>分析 GPU 使用量 (Direct3D)

在 Direct3D 應用程式中 (Direct3D 元件必須為 C++)，您可以檢查 GPU 上的活動並分析效能問題。 如需詳細資訊，請參閱 [GPU 使用量](./gpu-usage.md)。 若要使用此工具，請選擇效能分析工具中的 [GPU 使用量]，然後選擇 [開始]。 在應用程式中，完整瀏覽您想要分析的案例，然後選擇 [停止收集] 以產生報表。

當您在圖形中選擇一個時段，並選擇 [檢視詳細資料] 時，下方窗格即會顯示詳細的檢視。 在詳細的檢視中，您可以檢查每個 CPU 和 GPU 上發生多少活動。 您可以選取最下方窗格中的事件，取得時間軸的快顯功能表。 例如，選取 [Present] 事件以檢視 **Present** 呼叫快顯功能表   (淺灰色垂直 VSync 線可以作為參考，以瞭解是否 **有** 特定的呼叫遺漏 VSync。 每兩個 VSyncs 之間必須有一個 **目前** 的呼叫，應用程式才會穩定達到 60 FPS。 ) 

![GPU 使用量分析工具](../profiling/media/prof-tour-gpu-usage.png "診斷 GPU 使用量")

您也可以使用圖形來判斷是否有佔用 CPU 或 GPU 資源的效能瓶頸。

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>分析效能 (JavaScript UWP)

針對 UWP 應用程式，您可以使用 JavaScript 記憶體工具與 HTML UI 回應性工具。

JavaScript 記憶體工具和其他應用程式類型提供的記憶體使用量工具很類似。 您可以使用這項工具來了解記憶體使用量，並找出應用程式的記憶體流失情況。 如需此工具的詳細資訊，請參閱 [JavaScript 記憶體](../profiling/javascript-memory.md)。

![JavaScript 記憶體分析工具](../profiling/media/diagjsmemory.png "DiagJSMemory")

若要診斷 UWP 應用程式中的 UI 回應性、慢速載入時間，以及慢速視覺效果更新等問題，請使用 HTML UI 回應性工具。 其使用方式類似於其他應用程式類型的應用程式時間軸工具。 如需詳細資訊，請參閱 [HTML UI 回應性](../profiling/html-ui-responsiveness.md)。

![HTML UI 回應性分析工具](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>分析網路使用量 (UWP)

在 UWP 應用程式中，您可以使用 API 來分析執行的網路作業 `Windows.Web.Http` 。 此工具可協助您解決問題，例如存取和驗證問題、不正確的快取使用，以及不佳的顯示和下載效能。 若要使用此工具，請選擇 [效能分析工具] 中的 [網路]，然後選擇 [開始]。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集] 以產生報表。

![網路流量分析工具](../profiling/media/prof-tour-network-usage.png "診斷網路使用量")

選取摘要檢視中的作業，以檢視更多詳細資料。

![網路使用量工具中的詳細資訊](../profiling/media/prof-tour-network-usage-details.png "診斷網路使用量詳細資料")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>分析效能 (舊版工具)

::: moniker range="vs-2017"
如果您是執行桌面或 ASP.NET 應用程式，但 [CPU 使用量工具] 或 [記憶體使用量] 工具目前未顯示您需要的功能 (例如檢測)，則可以使用 [效能總管] 來進行分析  (UWP 應用程式不支援此功能)。 如需詳細資訊，請參閱[效能總管](../profiling/performance-explorer.md)。
::: moniker-end

::: moniker range=">=vs-2019"
在 Visual Studio 2019 中，舊版效能總管和相關的分析工具（例如 Performance Wizard）已折迭至效能分析工具，您可以使用 **Debug** 效能分析工具來開啟此功能  >  ****。 在效能分析工具中，可用的診斷工具取決於所選目標和目前開啟的啟始專案。 [CPU 使用量] 工具提供之前在效能分析工具中支援的取樣功能。 偵查工具會提供已檢測的程式碼剖析功能， (用於效能 Wizard 中的精確呼叫計數和持續時間) 。 額外的記憶體工具也會出現在效能分析工具中。
::: moniker-end

![效能總管工具](../profiling/media/prof-tour-performance-explorer.png "效能總管")

## <a name="which-tool-should-i-use"></a>應該使用哪一種工具？

以下資料表列出 Visual Studio 提供的各種工具和您可以用它們處理的不同專案類型︰

::: moniker range=">=vs-2019"
|效能工具|Windows 桌面|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[效能提示](../profiling/perftips.md)|是|是|是|
|[CPU 使用量](../profiling/beginners-guide-to-performance-profiling.md)|是|是|是|
|[記憶體使用量](../profiling/memory-usage.md)|是|是|是|
|[.NET 物件配置](../profiling/dotnet-alloc-tool.md)|是 ( 僅限 .NET) |是|是|
|[GPU 使用量](./gpu-usage.md)|是|是|否|
|[應用程式時間軸](../profiling/application-timeline.md)|是 (XAML) |是|否|
|[事件檢視器](../profiling/events-viewer.md)|是|是|是|
|[.NET Async](../profiling/analyze-async.md)|是 ( 僅限 .NET) |是|是|
|[.NET 計數器](../profiling/dotnet-counters-tool.md)|是 ( 僅限 .NET Core) |否|是 (只 ASP.NET Core) |
|[資料庫](../profiling/analyze-database.md)|是 ( 僅限 .NET Core) |否|是 (只 ASP.NET Core) |
|[效能總管](#analyze-performance-legacy-tools)|否|否|否|
|[IntelliTrace](../debugger/intellitrace.md)|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|效能工具|Windows 桌面|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU 使用量](../profiling/beginners-guide-to-performance-profiling.md)|是|是|是|
|[記憶體使用量](../profiling/memory-usage.md)|是|是|是|
|[GPU 使用量](./gpu-usage.md)|是|是|否|
|[應用程式時間軸](../profiling/application-timeline.md)|是 (XAML) |是|否|
|[效能提示](../profiling/perftips.md)|是|對 XAML 為是，對 HTML 為否|是|
|[效能總管](../profiling/performance-explorer.md)|是|否|是|
|[IntelliTrace](../debugger/intellitrace.md)|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|
|[網路使用量](../profiling/network-usage.md)|否|是|否|
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|否|對 HTML 為是，對 XAML 為否|否|
|[JavaScript 記憶體](../profiling/javascript-memory.md)|否|對 HTML 為是，對 XAML 為否|否|
::: moniker-end


## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)