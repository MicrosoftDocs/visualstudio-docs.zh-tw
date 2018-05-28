---
title: 在 Visual Studio 中分析 CPU 使用量 | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70ecd6517878800a6ad43221556c367137a64a71
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="analyze-cpu-usage"></a>分析 CPU 使用量
當您需要調查應用程式的效能問題時，了解應用程式如何使用 CPU 是不錯的起點。 「CPU 使用量」工具顯示 CPU 花時間執行 Visual C++、Visual C#/Visual Basic 和 JavaScript 程式碼的地方。 從 Visual Studio 2015 Update 1 開始，您不需要離開偵錯工具，就可以看到依函式的 CPU 使用量明細。 您可以在偵錯時開啟和關閉 CPU 分析，並檢視執行停止時的結果，例如中斷點。  
  
若要執行和管理診斷工作階段，您有幾個選項可以採用。 例如，您可以在本機或遠端電腦上，或在模擬器 (Simulator 或 Emulator) 中執行「CPU 使用量」 工具。 您可以分析在 Visual Studio 中開啟之專案的效能，附加至執行中的應用程式，或啟動從 Microsoft Store 安裝的應用程式。 如需詳細資訊，請參閱[搭配或不搭配偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

此處，我們會說明如何收集並分析發行組建的 CPU 使用量。 若要在偵錯期間分析 CPU 使用量，請參閱[效能分析的初學者指南](../profiling/beginners-guide-to-performance-profiling.md)。 

> [!NOTE]
> 如果是 .NET Core 和 ASP.NET Core，[CPU 使用量] 工具目前不提供使用可攜式 PBD 的精確結果。 請改用完整 PDB。
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> 收集 CPU 使用量資料  
  
1.  在 Visual Studio 中，將方案組態設定為 [發行] 並選擇部署目標。  
  
     ![選取版本和本機電腦](../profiling/media/cpuuse_selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
    -   在 [發行] 模式中執行應用程式，可讓您更清楚地檢視應用程式的實際效能。  
  
    -   在本機電腦上執行應用程式最適合重現已安裝應用程式的執行。  
  
    -   如果您從遠端裝置收集資料，請在裝置上直接執行應用程式，而不是使用遠端桌面連接。  
  
    -   對於 Windows Phone 應用程式，直接從 [裝置] 收集資料會提供最精確的資料。  
  
2.  在 [偵錯] 功能表上選擇 [效能分析工具]。  
  
3.  選擇 [CPU 使用量] ，然後選擇 [啟動]。  
  
     ![選擇 CPU 使用量](../profiling/media/cpuuse_lib_choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4.  當應用程式啟動時，按一下 [取得最大數目]。 在顯示輸出之後等候約 1 秒，然後選擇 [取得最大數目非同步] 。 在按鈕點選之間等候，可讓您更輕鬆地隔離診斷報告中的按鈕點選常式。  
  
5.  第二個輸出行出現之後，請選擇效能和診斷中樞中的 [停止收集]  。  
  
 ![停止 CpuUsage 資料收集](../profiling/media/cpu_use_wt_stopcollection.png "CPU_USE_WT_StopCollection")  
  
 CPU 使用量工具會分析資料，以及顯示報告。  
  
 ![CpuUsage 報表](../profiling/media/cpu_use_wt_report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>分析 CPU 使用量報告  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> CPU 使用量呼叫樹狀圖  
 若要開始了解呼叫樹狀圖資訊，請重新選取 `GetMaxNumberButton_Click` 區段，然後查看呼叫樹狀圖詳細資料。  
  
####  <a name="BKMK_Call_tree_structure"></a> 呼叫樹狀圖結構  
 ![GetMaxNumberButton&#95;Click 呼叫樹狀圖](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![步驟 1](../profiling/media/procguid_1.png "ProcGuid_1")|CPU 使用量呼叫樹狀圖中的最上層節點是虛擬節點|  
|![步驟 2](../profiling/media/procguid_2.png "ProcGuid_2")|在大部分的應用程式中，停用 [顯示外部程式碼]  選項時，第二層節點是一個含有系統和 Framework 程式碼的 [外部程式碼]  節點，而系統和 Framework 程式碼會啟動和停止應用程式、繪製 UI、控制執行緒排程，以及提供應用程式的其他低階服務。|  
|![步驟 3](../profiling/media/procguid_3.png "ProcGuid_3")|第二層節點的子系是第二層系統和 Framework 程式碼所呼叫或建立的使用者程式碼方法和非同步常式。|  
|![步驟 4](../profiling/media/procguid_4.png "ProcGuid_4")|某個方法的子節點只包含父系方法呼叫的資料。 停用 [顯示外部程式碼]  時，應用程式方法也可包含 [外部程式碼]  節點。|  
  
####  <a name="BKMK_External_Code"></a> 外部程式碼  
 外部程式碼是在系統和架構元件中由您撰寫之程式碼所執行的函式。 外部程式碼包含啟動和停止應用程式、繪製 UI、控制執行緒，以及將其他低階服務提供給應用程式的函式。 在大多數情況下，您對外部程式碼並不感興趣，因此 [CPU 使用量] 呼叫樹狀結構會將使用者方法的外部函式，收集成一個 [外部程式碼] 節點。  
  
 當您想要檢視外部程式碼的呼叫路徑時，請從 [篩選檢視]  清單中選擇 [顯示外部程式碼]  ，然後選擇 [套用] 。  
  
 ![選擇 [篩選檢視]，然後選擇 [ 顯示外部程式碼]](../profiling/media/cpu_use_wt_filterview.png "CPU_USE_WT_FilterView")  
  
 請注意，許多外部程式碼呼叫鏈結都是深度巢狀的，因此 [函式名稱] 資料行的寬度可能會超出所有電腦監視器 (但不含最大的電腦監視器) 的顯示寬度。 發生此情況時，函式名稱會顯示為 […]：  
  
 ![呼叫樹狀圖中的巢狀外部程式碼](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 使用搜尋方塊尋找您所尋找的節點，然後使用水平捲軸檢視資料：  
  
 ![搜尋巢狀外部程式碼](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> 呼叫樹狀圖資料行  
  
|||  
|-|-|  
|**CPU 總計 (%)**|![總計 % 資料方程式](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> 在選取的時間範圍內，函式的呼叫和該函式所呼叫的函式所使用的應用程式 CPU 活動百分比。 請注意，這與 [CPU 使用率]  時間軸圖表不同，後者會將時間範圍內的應用程式活動總計與可用的 CPU 容量總計進行比較。|  
|**自我 CPU (%)**|![自我 % 方程式](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> 在選取的時間範圍內，函式的呼叫所使用的應用程式 CPU 活動百分比 (不包括該函式所呼叫的函式活動)。|  
|**CPU 總計 (毫秒)**|在選取的時間範圍內，函式的呼叫和該函式所呼叫的函式所花費的毫秒數。|  
|**自我 CPU (毫秒)**|在選取的時間範圍內，函式的呼叫和該函式所呼叫的函式所花費的毫秒數。|  
|**模組**|內含函式的模組名稱，或內含 [外部程式碼] 節點中的函式的模組數目。|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU 使用量呼叫樹狀圖中的非同步函式  
 當編譯器發現非同步方法時，它會建立隱藏的類別來控制方法的執行。 就概念而言，這個類別是包含編譯器所產生之函式清單的狀態機器，這些函式會以非同步方式呼叫原始方法的作業，以及正常執行作業所需的回呼、排程器和迭代器。 父方法呼叫原始方法時，執行階段會從父系的執行內容中移除該方法，並在可控制應用程式執行的系統和 Framework 程式碼內容中執行隱藏類別的方法。 非同步方法通常 (但不一定永遠) 會在一個或多個不同的執行緒上執行。 這段程式碼會在 [CPU 使用量] 呼叫樹狀圖中，顯示為樹狀圖最上層節點正下方之 [外部程式碼]  節點的子系。  
  
 若要在範例中查看此情況，請重新選取時間軸中的 `GetMaxNumberAsyncButton_Click` 區段。  
  
 ![GetMaxNumberAsyncButton&#95;Click 報表選取項目](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 [外部程式碼]  下的前兩個節點是狀態機器類別之編譯器產生的方法。 第三個節點是原始方法的呼叫。 展開產生的方法可顯示正在進行的作業。  
  
 ![展開的 GetMaxNumberAsyncButton&#95;Click 呼叫樹狀圖](../profiling/media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` 的功能很有限；它會管理工作值清單、計算結果的最大值，並顯示輸出。  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` 會顯示排程和啟動將呼叫包裝至 `GetNumberAsync`之 48 項工作所需的活動。  
  
-   `MainPage::<GetNumberAsync>b__b` 會顯示呼叫 `GetNumber`之所有工作的活動。
