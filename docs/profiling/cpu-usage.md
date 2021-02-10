---
title: 分析效能分析工具中的 CPU 使用量
description: '瞭解 CPU 使用量效能工具，此工具會顯示在 c + +、c #、Visual Basic 和 JavaScript 應用程式中執行程式碼所花費的 CPU 時間和百分比。'
ms.custom: SEO-VS-2020
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a223a2007d62b84f06191c71523b861f94efe3d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956122"
---
# <a name="analyze-cpu-usage-without-debugging-in-the-performance-profiler"></a>在效能分析工具中分析 CPU 使用量，而不進行調試

要開始調查應用程式中效能問題的好方法是了解其 CPU 使用量。 [CPU 使用量] 效能工具顯示花在 C++、C#/Visual Basic 和 JavaScript 應用程式中執行程式碼的 CPU 時間和百分比。

[CPU 使用量] 工具可以在開啟的 Visual Studio 專案上及已安裝的 Microsoft Store 應用程式上執行，或是附加至執行中的應用程式或處理程序。 執行 [CPU 使用量] 工具時不一定需要包含偵錯。 如需詳細資訊，請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

下列指示說明如何使用 [CPU 使用量] 工具而不搭配偵錯工具，並且使用 Visual Studio [效能分析工具]。 範例使用在本機電腦上的 [發行] 組建。 [發行] 組建提供實際應用程式效能的最佳檢視。 若要使用偵錯工具附加)  (偵錯工具來分析 CPU 使用量，請參閱 [效能分析的初學者指南](../profiling/beginners-guide-to-performance-profiling.md)。

通常，本機電腦最能充分複製已安裝的應用程式執行。 若要從遠端裝置收集資料，請直接在裝置上執行應用程式，而不要透過遠端桌面連線。

>[!NOTE]
>需要 Windows 7 或更新版本才能使用[效能分析工具](../profiling/profiling-feature-tour.md)。

## <a name="collect-cpu-usage-data"></a>收集 CPU 使用量資料

1. 在 Visual Studio 專案中，將 [方案設定] 設定為 [ **發行** ]，然後選取 [ **本機 Windows 偵錯工具** ] (或 [ **本機電腦** ]) 作為部署目標。

    ![選取版本和本機電腦](../profiling/media/cpuuse_selectreleaselocalmachine.png "選取版本和本機電腦")

1. 選取 [ **Debug**  >  **效能分析工具**]。

1. 在 [可用的工具] 下，選取 [CPU 使用量]，然後選取 [啟動]。

    ![選取 CPU 使用量](../profiling/media/cpuuse_lib_choosecpuusage.png "選取 CPU 使用量")

4. 應用程式啟動之後，診斷工作階段會開始，並顯示 CPU 使用量資料。 當您完成收集資料時，請選取 [停止收集]。

   ![停止 CPU 使用量資料收集](../profiling/media/cpu_use_wt_stopcollection.png "停止 CPU 使用量資料收集")

   CPU 使用量工具會分析資料，以及顯示報告。

   ![CPU 使用量報表](../profiling/media/cpu_use_wt_report.png "CPU 使用量報表")

## <a name="analyze-the-cpu-usage-report"></a>分析 CPU 使用量報告

診斷報表的排序是依據 [CPU 總計]，從最高到最低。 選取資料行標頭，即可變更排序順序或排序資料行。 使用 [篩選條件] 下拉式清單來選取或取消選取要顯示的執行緒，並使用 [搜尋] 方塊來搜尋特定執行緒或節點。

::: moniker range=">=vs-2019"
從 Visual Studio 2019 開始，您可以按一下 [展開最忙碌路徑] 和 [顯示最忙碌路徑] 按鈕，以查看在呼叫樹狀檢視中使用最高 CPU 百分比的函式呼叫。
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> [CPU 使用量] 資料行

|名稱|描述|
|-|-|
|**CPU 總計 [單位, %]**|![總計 % 資料方程式](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> 在選取的時間範圍內，呼叫函式和該函式所呼叫函式使用的毫秒數及 CPU 百分比。 這與 [CPU 使用率]  時間軸圖表不同，其會將時間範圍內的 CPU 活動總計與可用的 CPU 總計進行比較。|
|**自我 CPU [單位, %]**|![自我 % 方程式](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> 在選取的時間範圍內，呼叫函式使用的毫秒數及 CPU 百分比，不包含函式所呼叫的函式。|
|**模組**|包含函式的模組名稱。

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> CPU 使用量呼叫樹狀圖

若要檢視呼叫樹狀結構，請在報表中選取父節點。 [CPU 使用量] 頁面會開啟至 [呼叫者/被呼叫者] 檢視。 在 [目前的檢視] 下拉式清單中，選取 [呼叫樹狀結構]。

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> 呼叫樹狀圖結構

::: moniker range=">=vs-2019"
![呼叫樹狀結構](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "呼叫樹狀圖結構")
::: moniker-end
::: moniker range="vs-2017"
![呼叫樹狀結構](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "呼叫樹狀圖結構")
::: moniker-end

|映像|描述|
|-|-|
|![步驟 1](../profiling/media/procguid_1.png "ProcGuid_1")|[CPU 使用量] 呼叫樹狀結構中的最上層節點是一個虛擬節點。|
|![步驟 2](../profiling/media/procguid_2.png "ProcGuid_2")|在大部分的應用程式中，已停用 [顯示外部程式碼] 選項時，第二層節點是一個 [外部程式碼] 節點。 節點包含系統和架構程式碼，程式碼會啟動和停止應用程式、繪製 UI、控制執行緒排程，並提供其他低階服務給應用程式。|
|![步驟 3](../profiling/media/procguid_3.png "ProcGuid_3")|第二層節點的子系是第二層系統和 Framework 程式碼所呼叫或建立的使用者程式碼方法和非同步常式。|
|![步驟4](../profiling/media/procguid_4.png "ProcGuid_4")|某個方法的子節點只有父方法呼叫的資料。 停用 [顯示外部程式碼]  時，應用程式方法也可包含 [外部程式碼]  節點。|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> 外部程式碼

您程式碼所執行的系統和架構函式稱為「外部程式碼」。 外部程式碼函式會啟動和停止應用程式、繪製 UI、控制執行緒，以及將其他低階服務提供給應用程式。 在大多數情況下，您對外部程式碼並不感興趣，因此 [CPU 使用量] 呼叫樹狀結構會將使用者方法的外部函式，收集成一個 [外部程式碼] 節點。

若要檢視外部程式碼的呼叫路徑，在主要診斷報表頁面上 (右窗格)，從 [篩選條件] 下拉式清單中選取 [顯示外部程式碼]，然後選取 [套用]。 [CPU 使用量] 頁面的 [呼叫樹狀結構] 檢視會展開外部程式碼呼叫。 ([篩選條件] 下拉式清單提供於主要診斷頁面而非詳細檢視上。)

![顯示外部程式碼](../profiling/media/cpu_use_wt_filterview.png "顯示外部程式碼")

許多外部程式碼呼叫鏈結為深度巢狀，因此鏈結的寬度可能會超出 [函式名稱] 資料行的顯示寬度。 函式名稱則會顯示為 **...**。

![呼叫樹狀結構中的巢狀外部程式碼](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "呼叫樹狀結構中的巢狀外部程式碼")

若要找到您正在尋找的函式名稱，請使用搜尋方塊。 暫留在選取的行，或使用水平捲軸來檢視資料。

::: moniker range=">=vs-2019"
![搜尋巢狀外部程式碼](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "搜尋巢狀外部程式碼")
::: moniker-end
::: moniker range="vs-2017"
![搜尋巢狀外部程式碼](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "搜尋巢狀外部程式碼")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU 使用量呼叫樹狀結構中的非同步函式

 當編譯器發現非同步方法時，它會建立隱藏的類別來控制方法的執行。 就概念而言，類別是狀態機器。 類別具有編譯器產生的函式，以非同步方式呼叫原始方法，以及若要執行它們所需的回呼、排程器和迭代器。 父方法呼叫原始方法時，編譯器會從父代的執行內容移除該方法，並在控制應用程式執行的系統和架構程式碼內容中執行隱藏類別方法。 非同步方法通常 (但不一定永遠) 會在一個或多個不同的執行緒上執行。 這段程式碼會在 [CPU 使用量] 呼叫樹狀結構中，顯示為樹狀結構最上層節點正下方 [外部程式碼] 節點的子系。

在下列範例中，[外部程式碼] 下的前兩個節點是狀態機器類別的編譯器產生方法。 第三個節點是原始方法的呼叫。

![非同步節點](media/cpu_use_wt_getmaxnumberasync_selected.png "非同步節點")

展開所產生方法以顯示正在進行的作業：

![展開的非同步節點](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "展開的非同步節點")

- `MainPage::GetMaxNumberAsyncButton_Click` 只會管理工作值清單、計算結果的最大值，並顯示輸出。

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` 會顯示排程和啟動將呼叫包裝至 `GetNumberAsync`之 48 項工作所需的活動。

- `MainPage::<GetNumberAsync>b__b` 會顯示呼叫 `GetNumber`之工作的活動。
