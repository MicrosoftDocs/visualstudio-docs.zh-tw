---
title: 利用分析工具測量效能
description: 查看 Visual Studio 中可用的各種診斷工具。
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1ee476a518444bfff7a97a12c9fd814e9509239
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2020
ms.locfileid: "80412029"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>快速入門：初步認識分析工具

Visual Studio 提供各種不同的分析工具，可協助您依據應用程式類型來診斷不同類型的效能問題。

您可以在偵錯工作階段期間，存取 [診斷工具] 視窗提供的分析工具。 [診斷工具] 視窗會自動出現，除非您將其關閉。 如需顯示視窗，請按一下 [偵錯]/[視窗]/[顯示診斷工具]****。 視窗開啟時，您可以選取要用來收集資料的工具。

![診斷工具視窗](../profiling/media/prof-tour-diagnostic-tools.png "診斷工具")

在進行偵錯期間，您可以使用 [診斷工具]**** 視窗，分析 CPU 和記憶體使用量，您也可以檢視顯示效能相關資訊的事件。

![診斷工具 摘要檢視](../profiling/media/prof-tour-cpu-and-memory-graph.gif "診斷工具摘要")

若要分析您的應用程式，通常的慣用方法是使用 [診斷工具]**** 視窗，但您也可以針對發行組建改為執行應用程式的事後剖析分析。 如需不同方法的詳細資訊，請參閱[使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 若要查看針對不同應用程式類型的分析工具支援，請參閱[應該使用哪一種工具？](#which-tool-should-i-use)

> [!NOTE]
> 您可以在 Windows 7 及更新版本中使用事後分析工具。 Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具]**** 視窗)。

## <a name="examine-performance-using-perftips"></a>使用 PerfTips 檢查效能

通常,檢視效能資訊的最簡單方法是使用[PerfTips](../profiling/perftips.md)。 使用 PerfTips,您可以在與程式碼互動時查看性能資訊。 您可以檢查事件持續時間等資訊 (從上次暫停偵錯工具或應用程式啟動時開始測量)。 例如,如果您單步執行代碼(F10、F11),PerfTips 會顯示從上一步操作到當前步驟的應用運行時持續時間。

![分析教學 PerfTips](../profiling/media/prof-tour-perf-tips.png "分析教學 PerfTips")

可以使用 PerfTips 檢查代碼塊執行所需的時間,或者單個函數完成所需的時間。

PerfTips 顯示診斷工具**的事件**檢視中也顯示的相同事件。 在 **「事件」** 檢視中,您可以查看除錯時發生的不同事件,例如斷點設定或代碼步進操作。

![診斷工具事件檢視](../profiling/media/prof-tour-events.png "診斷工具檢視事件")

 > [!NOTE]
 > 如果您有 Visual Studio Enterprise，也可以查看這個索引標籤中的 [IntelliTrace 事件](../debugger/intellitrace.md)。

## <a name="analyze-cpu-usage"></a>分析 CPU 使用

CPU 使用量工具是您開始分析應用程式效能的最佳入門。 它會告訴您應用程式耗用的 CPU 資源詳細資訊。 有關 CPU 使用工具的更詳細的演練,請參閱[透過分析 CPU 使用方式來測量應用程式效能](../profiling/beginners-guide-to-performance-profiling.md)。

從 [診斷工具] 的 [摘要]**** 檢視中，選擇 [啟用 CPU 分析]**** \(必須在偵錯工作階段中)。

![在診斷工具中啟用 CPU 使用率](../profiling/media/prof-tour-enable-cpu-profiling.png "診斷工具支援 CPU 使用")

若要以最有效的方式使用工具，請為您的程式碼設定兩個中斷點：一個在函式開頭，一個在函式結尾 (或您想要分析的程式碼區域)。 當您在第二個中斷點上暫停時，即可檢查分析資料。

[CPU 使用量]**** 檢視會顯示一份執行時間最長的函式清單，並將時間最長的放在頂端來排序。 這可協助引導您找出發生效能瓶頸的函式。

![診斷工具 CPU 使用情況檢視](../profiling/media/prof-tour-cpu-usage.png "診斷工具 CPU 使用方式")

按兩下要查看的函式，即會看到更詳細的三個窗格「蝶型」檢視：視窗中間為已選取的函式、左側為發出呼叫的函式，右側為接收呼叫的函式。 [函式主體]**** 區段會顯示函式主體所花費的總時間 (和時間百分比)，但不包括發出呼叫的函式和接收呼叫的函式所花的時間。 這項資料可協助您評估函式本身是否有效能瓶頸。

![診斷工具呼叫者「蝴蝶」檢視](../profiling/media/prof-tour-cpu-usage-caller-callee.png "診斷工具 呼叫方呼叫者檢視")

## <a name="analyze-memory-usage"></a>分析記憶體使用量

「**診斷工具」** 視窗還允許您使用 **「記憶體使用方式**」工具評估應用中的記憶體使用方式。 例如，您可以查看堆積的物件數目和大小。 有關分析記憶體的更多詳細說明,請參閱[分析記憶體使用方式](../profiling/memory-usage.md)。 另一個記憶體分析工具[.NET 物件分配工具](../profiling/dotnet-alloc-tool.md)可説明您識別 .NET 代碼中的分配模式和異常。

要使用調試器集成的記憶體使用方式分析記憶體使用方式,至少需要拍攝一個記憶體快照。 通常，分析記憶體的最佳方式是擷取兩個快照：第一個快照是在可能發生記憶體問題之前擷取，第二個快照則是緊接在可能發生記憶體問題之後擷取。 然後您可以檢視兩個快照的差異，並查看其中到底有什麼變更。

![在診斷工具中拍攝快照](../profiling/media/prof-tour-take-snapshots.gif "診斷工具 拍攝快照")

當您選擇其中一個箭頭連結時,系統會為您提供堆的差分視圖(紅色向上箭頭![記憶體使用量增加](../profiling/media/prof-tour-mem-usage-up-arrow.png "記憶體使用量增加")顯示增加的物件計數(左)或增加的堆大小(右)。 如果您按一下右邊的連結，即會取得差異堆積檢視，該檢視會以堆積大小增加最多的物件來排序。 這麼做有助您鎖定記憶體的問題。 如下圖所示，`ClassHandlersStore` 物件使用的位元組在第二張快照中增加了 3,492 個位元組。

![診斷工具堆差異檢視](../profiling/media/prof-tour-mem-usage-diff-heap.png "診斷工具堆差異檢視")

如果您按一下左側的連結，而不是 [記憶體使用量]**** 檢視，堆積檢視就會依照物件計數來組織；數目增加最多的特定類型物件會顯示在頂端 (依 [計數差異]**** 資料行排序)。

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a> 不使用偵錯工具來分析發行組建

分析工具 (如 CPU 使用率和記憶體使用量) 可與偵錯工具搭配使用 (請參閱稍早章節)，或者，您可以使用專為**發行**組建提供分析的效能分析工具，在事後執行分析工具。 使用效能分析工具時，您可以在執行應用程式時收集診斷資訊，並在應用程式停止之後檢查所收集的資訊。 如需不同方法的詳細資訊，請參閱[使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 效能探查器中提供其他工具,如[.NET 物件配置工具](../profiling/dotnet-alloc-tool.md)。

![效能分析工具](../profiling/media/prof-tour-performance-profiler.png "效能分析工具")

以選擇**除錯** > **效能探查器開啟效能探查器**。

在某些情況下，您可以透過此視窗選取多個分析工具。 [CPU 使用量] 這類工具也可以提供有助於分析的補充資料。 您還可以使用[命令列探查器](../profiling/profile-apps-from-command-line.md)啟用涉及多個分析工具的方案。

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>檢查 UI 效能和協助工具事件 (UWP)

在 UWP 應用程式中,您可以在 **「診斷工具」** 視窗中啟用**UI 分析**。 此工具會搜尋常見的效能或協助工具問題，並於偵錯時將問題顯示在 [事件]**** 檢視中。 事件描述提供有助您解決問題的相關資訊。

![檢視工具中檢視 UI 分析事件](../profiling/media/prof-tour-ui-analysis.png "診斷工具檢視 UI 分析事件")

## <a name="analyze-resource-consumption-xaml"></a>分析資源取用量 (XAML)

在 XAML 應用程式 (例如 Windows 傳統型 WPF 應用程式和 UWP App) 中，您可以使用應用程式時間軸工具來分析資源耗用量。 例如，您可以分析應用程式準備 UI 畫面格 (版面配置和轉譯)、服務網路和磁碟要求，以及像是應用程式啟動、頁面載入和視窗大小調整等情況所花費的時間。 若要使用此工具，請選擇 [效能分析工具] 中的 [應用程式時間軸]****，然後選擇 [開始]****。 在應用程式中，完整瀏覽具有可疑資源消耗問題的案例，然後選擇 [停止收集]**** 以產生報表。

如果您執行應用程式時出現視覺化的問題，其可能反應在 [視覺輸送量]**** 圖形中的低畫面播放速率。 同樣地，若出現 UI 回應性問題，也可能會反應在 [UI 執行緒使用率]**** 圖形中居高的數字。 您可以在報表中針對可疑的效能問題選擇一個時段，然後檢查 [時間軸] 詳細資料檢視 (下方窗格) 中的詳細 UI 執行緒活動。

![應用程式時間線分析工具](../profiling/media/prof-tour-application-timeline.gif "分析巡視應用程式時間線")

在「時間軸詳細資訊」檢視中,您可以查找活動類型(或所涉及的 UI 元素)以及活動的持續時間等資訊。 例如，圖例中，格線控制項的 [配置]**** 事件花了 57.53 毫秒。

如需詳細資訊，請參閱[應用程式時間軸](../profiling/application-timeline.md)。

## <a name="analyze-gpu-usage-direct3d"></a>分析 GPU 使用量 (Direct3D)

在 Direct3D 應用程式中 (Direct3D 元件必須為 C++)，您可以檢查 GPU 上的活動並分析效能問題。 如需詳細資訊，請參閱 [GPU 使用量](/visualstudio/debugger/graphics/gpu-usage)。 若要使用此工具，請選擇效能分析工具中的 [GPU 使用量]****，然後選擇 [開始]****。 在應用程式中，完整瀏覽您想要分析的案例，然後選擇 [停止收集]**** 以產生報表。

當您在圖形中選擇一個時段，並選擇 [檢視詳細資料]**** 時，下方窗格即會顯示詳細的檢視。 在詳細的檢視中，您可以檢查每個 CPU 和 GPU 上發生多少活動。 您可以選取最下方窗格中的事件，取得時間軸的快顯功能表。 例如，選取 [Present]**** 事件以檢視 **Present** 呼叫快顯功能表  (您可以參考淺灰色垂直 Vsync 線，藉此了解特定 **Present** 呼叫是否錯過了 Vsync。 每兩條 Vsync 之間必須有一個 **Present** 呼叫，以讓應用程式穩定地達到 60 FPS。)

![GPU 使用分析工具](../profiling/media/prof-tour-gpu-usage.png "診斷 GPU 使用")

您也可以使用圖形來判斷是否有佔用 CPU 或 GPU 資源的效能瓶頸。

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>分析效能 (JavaScript UWP)

針對 UWP 應用程式，您可以使用 JavaScript 記憶體工具與 HTML UI 回應性工具。

JavaScript 記憶體工具和其他應用程式類型提供的記憶體使用量工具很類似。 您可以使用這項工具來了解記憶體使用量，並找出應用程式的記憶體流失情況。 如需此工具的詳細資訊，請參閱 [JavaScript 記憶體](../profiling/javascript-memory.md)。

![JavaScript 記憶體分析工具](../profiling/media/diagjsmemory.png "迪亞吉斯記憶")

若要診斷 UWP 應用程式中的 UI 回應性、慢速載入時間，以及慢速視覺效果更新等問題，請使用 HTML UI 回應性工具。 其使用方式類似於其他應用程式類型的應用程式時間軸工具。 如需詳細資訊，請參閱 [HTML UI 回應性](../profiling/html-ui-responsiveness.md)。

![HTML UI 回應性分析工具](../profiling/media/diaghtmlresp.png "迪亞格HTML雷斯普")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>分析網路使用量 (UWP)

在 UWP 應用程式中，您可以使用 `Windows.Web.Http` API 來分析執行的網路作業。這項工具有助您解決存取及驗證問題、不正確的快取使用，以及不良的顯示和下載效能等問題。 若要使用此工具，請選擇 [效能分析工具] 中的 [網路]****，然後選擇 [開始]****。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集]**** 以產生報表。

![網路使用方式分析工具](../profiling/media/prof-tour-network-usage.png "直徑網路使用")

選取摘要檢視中的作業，以檢視更多詳細資料。

![網路使用工具中的詳細資訊](../profiling/media/prof-tour-network-usage-details.png "Diag 網路使用詳細資訊")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>分析效能 (舊版工具)

::: moniker range="vs-2017"
如果您是執行桌面或 ASP.NET 應用程式，但 [CPU 使用量工具] 或 [記憶體使用量] 工具目前未顯示您需要的功能 (例如檢測)，則可以使用 [效能總管] 來進行分析  (UWP 應用程式不支援此功能)。 如需詳細資訊，請參閱[效能總管](../profiling/performance-explorer.md)。
::: moniker-end

::: moniker range=">=vs-2019"
在 Visual Studio 2019 中,舊版效能資源管理器和相關分析工具(如效能精靈)已摺疊到性能探查器中,您可以使用**調試** > **性能探查器**打開這些工具。 在性能探查器中,可用的診斷工具取決於所選的目標和當前打開的啟動專案。 CPU 使用工具提供性能精靈中以前支援的採樣功能。 "檢測"工具提供性能精靈中偵測的分析功能(用於精確的呼叫計數和持續時間)。 其他記憶體工具也出現在性能探查器中。
::: moniker-end

![效能資源管理員工具](../profiling/media/prof-tour-performance-explorer.png "效能總管")

## <a name="which-tool-should-i-use"></a>應該使用哪一種工具？

以下資料表列出 Visual Studio 提供的各種工具和您可以用它們處理的不同專案類型︰

::: moniker range=">=vs-2019"
|效能工具|Windows 桌面|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU 使用量](../profiling/cpu-usage.md)|是|是|是|
|[記憶體使用量](../profiling/memory-usage.md)|是|是|是|
|[.NET 物件配置](../profiling/dotnet-alloc-tool.md)|是(僅限.NET)|是|是|
|[GPU 使用量](/visualstudio/debugger/graphics/gpu-usage)|是|是|否|
|[應用程式時間軸](../profiling/application-timeline.md)|是|是|否|
|[「效能提示」](../profiling/perftips.md)|是|對 XAML 為是，對 HTML 為否|是|
|[效能總管](../profiling/performance-explorer.md)|是|否|是|
|[IntelliTrace](../debugger/intellitrace.md)|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|效能工具|Windows 桌面|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU 使用量](../profiling/cpu-usage.md)|是|是|是|
|[記憶體使用量](../profiling/memory-usage.md)|是|是|是|
|[GPU 使用量](/visualstudio/debugger/graphics/gpu-usage)|是|是|否|
|[應用程式時間軸](../profiling/application-timeline.md)|是|是|否|
|[「效能提示」](../profiling/perftips.md)|是|對 XAML 為是，對 HTML 為否|是|
|[效能總管](../profiling/performance-explorer.md)|是|否|是|
|[IntelliTrace](../debugger/intellitrace.md)|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|僅限 .NET 與 Visual Studio Enterprise|
|[網路使用量](../profiling/network-usage.md)|否|是|否|
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|否|對 HTML 為是，對 XAML 為否|否|
|[JavaScript 記憶體](../profiling/javascript-memory.md)|否|對 HTML 為是，對 XAML 為否|否|
::: moniker-end


## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯](../debugger/debugger-feature-tour.md)
