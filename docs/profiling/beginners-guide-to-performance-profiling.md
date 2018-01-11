---
title: "在 Visual Studio 中分析應用程式效能 | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords: vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: "45"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bacc4e9ebb0b0125b22089ec53a97248e9e1f4e9
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="profile-application-performance-in-visual-studio"></a>在 Visual Studio 中分析應用程式效能
您可以使用 Visual Studio 程式碼剖析工具來分析應用程式中的效能問題。 此程序示範如何使用 [診斷工具] 的 [CPU 使用量] 索引標籤，以取得您的應用程式的效能資料。 診斷工具可用於 Visual Studio 中的 .NET 開發 (包括 ASP.NET) 和原生/C++ 開發。
  
當偵錯工具暫停時，[CPU 使用量] 工具會收集在應用程式中執行的函式的詳細資訊。 此工具列出正在執行工作的函式，並提供讓您用來專注於取樣工作階段特定區段的時間軸圖形。

診斷中樞提供許多其他選項來執行和管理診斷工作階段。 如果 [CPU 使用量] 沒有提供您所需的資料，則[其他程式碼剖析工具](../profiling/Profiling-Tools.md)可提供不同種類的資訊，這可能會很有幫助。 在許多情況下，應用程式的效能瓶頸可能是 CPU 以外的問題所導致，例如記憶體、呈現 UI 或網路要求時間。 診斷中樞提供許多其他選項來記錄和分析這類資料。

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")  |    [觀看使用診斷工具的影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171)，了解如何分析 CPU 使用量，以及如何分析記憶體使用量。 |

在本主題中，我們將討論一般偵錯工作流程中的 CPU 使用量分析。 您也可以不附加偵錯工具或是以執行中的應用程式為目標來分析 CPU 使用量。如需詳細資訊，請參閱[使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)中的[收集分析資料但不偵錯](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)。
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> 步驟 1︰收集程式碼剖析資料 
  
1.  開啟您想要在 Visual Studio 中偵錯的專案，並在您的應用程式中要檢查 CPU 使用量的位置設定中斷點。

2.  在函式的結尾或您想要分析的程式碼區域設定第二個中斷點。

    > [!TIP]
    > 藉由設定兩個中斷點，您可以將資料收集的範圍限制在您想分析的程式碼部分。
  
3.  [偵錯工具]  視窗會自動出現，除非您將其關閉。 如需再次顯示視窗，請按一下 [偵錯/Windows/顯示診斷工具]。

4.  您可以透過工具列上的 [Select Tools (選取工具)] 設定來選擇是否要查看 [CPU Usage (CPU 使用量)]、[[Memory Usage (記憶體使用量)]](../profiling/Memory-Usage.md) 或 (或兩者)。 若正在執行 Visual Studio Enterprise，您也可以在 [工具/選項/IntelliTrace]  中啟用或停用 IntelliTrace。

     ![顯示診斷工具](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     我們主要是要查看 CPU 使用率，因此，請務必啟用 [CPU 使用量] (預設為啟用)。

5.  按一下 [偵錯/開始偵錯] (或工具列上的 [開始] 或 **F5**)。

     當應用程式完成載入時，會出現 [Diagnostics Tools (診斷工具)] 的 [Summary (摘要)] 檢視。

     ![診斷工具摘要索引標籤](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     如需事件的詳細資訊，請參閱[搜尋和篩選診斷工具視窗的事件索引標籤 (Searching and filtering the Events tab of the Diagnostic Tools window)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx)。

6.  執行會叫用您的第一個中斷點的案例。

7.  當偵錯工具暫停時，啟用 CPU 使用量資料的收集，然後開啟 [CPU Usage (CPU 使用量)] 索引標籤。

     ![診斷工具可啟用 CPU 分析](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     當您選擇 [記錄 CPU 分析] 時，Visual Studio 就會開始錄製您的函式以及它們所需的執行時間。 只有在應用程式於中斷點停止時，您才能檢視收集的資料。

8.  按 F5 使應用程式執行至第二個中斷點。

     現在，您擁有在兩個中斷點之間執行的程式碼區域專屬的應用程式效能資料。

9.  在 CPU 時間軸中選取您想要分析的區域 (必須是顯示程式碼剖析資料的區域)。

     ![選取一個時間區段的診斷工具](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     程式碼剖析工具隨即開始準備執行緒資料。 等候它完成。

     ![正在準備執行緒的診斷工具](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     [CPU 使用量] 工具會在 [CPU Usage (CPU 使用量)] 索引標籤中顯示報告。
  
     ![診斷工具 CPU 使用量索引標籤](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     此時，您可以開始分析資料。

## <a name="Step2"></a> 步驟 2：分析 CPU 使用量資料

建議您先檢查 [CPU 使用量] 下方的函式清單、識別執行最多工作的函式，仔細觀察每一項，接著開始分析您的資料。

1. 在函式清單中，檢查執行最多工作的函式。

    ![診斷工具 CPU 使用量函式清單](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > 執行工作最多的函式會優先列出 (不是以呼叫順序列出)。 這可協助您快速找出執行時間最長的函式。

2. 在函式清單中，連按兩下執行大量工作的其中一個應用程式函式。

    當您按兩下函式時，[Caller/Callee (呼叫者/被呼叫者)] 檢視會在左窗格中開啟。 

    ![診斷工具的呼叫端/被呼叫端檢視](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    在此檢視中，選取的函式會出現在標題和 [目前的函式] 方塊中 (在此範例中為 GetNumber)。 呼叫目前函式的函式顯示在左邊的 [Calling Function (呼叫的函式)] 下方，而目前函式所呼叫的任何函式會顯示在右邊的 [Called Functions (所呼叫函式)] 方塊。 (您可以選取任一個方塊來變更目前的函式。)

    此檢視會顯示總時間 (毫秒) 及完成函式所需時間在整體應用程式執行時間所佔的百分比。
    [函式主體] 也會顯示函式主體所花費的總時間 (和時間百分比)，不包括呼叫的函式和所呼叫函式所花的時間。 (在此範例中，3729 毫秒中的 3713 毫秒花在函式主體，其餘 16 毫秒則花在此函式呼叫的外部程式碼)。

    > [!TIP]
    > [函式主體] 值高可能表示函式本身內有效能瓶頸。

3. 如果您想要查看較高層級的檢視 (以呼叫函式的順序顯示)，請從窗格上方的下拉式清單中選取 [呼叫樹狀圖]。
 
    圖中的每個編號區域與程序中的步驟相關。
  
    ![診斷工具呼叫樹狀圖](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![步驟 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU 使用量呼叫樹狀圖中的最上層節點是虛擬節點|  
|![步驟 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|在大部分的應用程式中，停用 [[顯示外部程式碼]](#BKMK_External_Code) 選項時，第二層節點是一個含有系統和 Framework 程式碼的 [外部程式碼]  節點，而系統和 Framework 程式碼會啟動和停止應用程式、繪製 UI、控制執行緒排程，以及提供應用程式的其他低階服務。|  
|![步驟 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|第二層節點的子系是第二層系統和 Framework 程式碼所呼叫或建立的使用者程式碼方法和非同步常式。|
|![步驟 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|某個方法的子節點只包含父系方法呼叫的資料。 停用 [顯示外部程式碼]  時，應用程式方法也可包含 [外部程式碼]  節點。|

以下是關於資料行值的詳細資訊︰

- [Total CPU (CPU 總計)] 表示函式及其呼叫的任何函式已完成多少工作。 高 CPU 總計值指向整體耗費最多資源的函式。
  
- [Self CPU (自我 CPU)] 表示函式主體中的程式碼已完成多少工作，但會排除其呼叫的函式所完成的工作。 [Self CPU (自我 CPU)] 值高可能表示函式本身內有效能瓶頸。

- [Modules (模組)] 內含函式的模組名稱，或內含 [External Code (外部程式碼)] 節點中的函式的模組數目。

## <a name="BKMK_External_Code"></a>檢視外部程式碼

外部程式碼是在系統和架構元件中由您撰寫之程式碼所執行的函式。 外部程式碼包含啟動和停止應用程式、繪製 UI、控制執行緒，以及將其他低階服務提供給應用程式的函式。 在大多數情況下，您對外部程式碼並不感興趣，因此 [CPU 使用量] 工具會將使用者方法的外部函式，收集成一個 [外部程式碼] 節點。
  
如果您想要檢視外部程式碼的呼叫路徑時，請從 [Filter (篩選)] 檢視清單中選擇 [Show External Code (顯示外部程式碼)]  ，然後選擇 [(Apply) 套用] 。  
  
![選擇 [Filter (篩選)]檢視，然後選擇 [Show External Code (顯示外部程式碼)]](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
請注意，許多外部程式碼呼叫鏈結都是深度巢狀的，因此 [函式名稱] 資料行的寬度可能會超出所有電腦監視器 (但不含最大的電腦監視器) 的顯示寬度。 發生此情況時，函式名稱會顯示為 […]：
  
使用搜尋方塊尋找您所尋找的節點，然後使用水平捲軸檢視資料。

> [!TIP]
> 如果您剖析呼叫 Windows 函式的外部程式碼，您應該要確定您有最新的 .pdb 檔案。 如果沒有這些檔案，您的報告檢視會列出隱晦且難以了解的 Windows 函式名稱。 如需如何確認您擁有所需檔案的詳細資訊，請參閱[在偵錯工具中指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。
  
## <a name="see-also"></a>請參閱  
 [記憶體使用量](../profiling/memory-usage.md)  
 [CPU 使用量](../profiling/cpu-usage.md)  
 [Visual Studio 中的分析](../profiling/index.md)  
 [程式碼剖析功能導覽](../profiling/profiling-feature-tour.md)
