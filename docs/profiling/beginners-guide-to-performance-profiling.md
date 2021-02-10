---
title: 測量您應用程式中的 CPU 使用量
description: 使用與偵錯工具整合的診斷工具來分析您應用程式中的 CPU 效能問題。
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a18302067749e3b4fc70b08519056dc391d3dca4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936882"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>透過分析 CPU 使用量測量應用程式效能

當您使用偵錯工具整合的 **CPU 使用量** 診斷工具進行偵錯工具時，尋找效能問題。  您也可以在不附加偵錯工具的情況下分析 CPU 使用量，或是以執行中的應用程式為目標。 如需詳細資訊，請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

當偵錯工具暫停時，診斷工具視窗中的 [ **CPU 使用量** ] 工具會收集在應用程式中執行之函式的相關資訊。 此工具列出正在執行工作的函式，並提供讓您用來專注於取樣工作階段特定區段的時間軸圖形。

> [!Important]
> 偵錯工具整合的診斷工具支援在 Visual Studio 中進行 .NET 開發，包括 ASP.NET、ASP.NET Core 和原生/c + + 開發。 Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具] 視窗)。

在本教學課程中，您將：

> [!div class="checklist"]
> * 收集 CPU 使用量資料
> * 分析 CPU 使用量資料

如果 **CPU 使用量** 未提供您所需的資料， [效能分析工具](../profiling/profiling-feature-tour.md#post_mortem) 中的其他程式碼剖析工具會提供可能對您有説明的不同資訊類型。 在許多情況下，應用程式的效能瓶頸可能是 CPU 以外的問題所導致，例如記憶體、呈現 UI 或網路要求時間。

## <a name="step-1-collect-profiling-data"></a>步驟 1︰收集分析資料

1. 開啟您想要在 Visual Studio 中偵錯的專案，並在您的應用程式中要檢查 CPU 使用量的位置設定中斷點。

2. 在函式的結尾或您想要分析的程式碼區域設定第二個中斷點。

    藉由設定兩個中斷點，您可以將資料收集的範圍限制在您想分析的程式碼部分。

3. 除非您已關閉 **診斷工具** 視窗，否則它會自動顯示。 若要再次顯示視窗，請按一下 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。

4. 您可以透過工具列上的 [Select Tools (選取工具)] 設定來選擇是否要查看 [CPU Usage (CPU 使用量)]、[Memory Usage (記憶體使用量)](../profiling/Memory-Usage.md) 或 (或兩者)。 如果您正在執行 Visual Studio Enterprise，也可以在 [**工具**  >  **選項**]  >  **intellitrace** 中啟用或停用 intellitrace。

     ![顯示診斷工具](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     我們主要是要查看 CPU 使用率，因此，請務必啟用 [CPU 使用量] (預設為啟用)。

5. 按一下 [ **Debug**  >  **開始** 錯 (] 或 [**啟動**] 工具列上的 [啟動]，或按 **F5**) 。

     當應用程式完成載入時，會出現 [Diagnostics Tools (診斷工具)] 的 [Summary (摘要)] 檢視。 如果您需要開啟視窗，請按一下 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。

     ![診斷工具摘要索引標籤](../profiling/media/diag-tools-summary-tab.png ">diagtoolssummarytab")

     如需事件的詳細資訊，請參閱 [診斷工具視窗的 [搜尋和篩選事件]](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)索引標籤。

6. 執行會叫用您的第一個中斷點的案例。

7. 當偵錯工具暫停時，啟用 CPU 使用量資料的收集，然後開啟 [CPU Usage (CPU 使用量)] 索引標籤。

     ![診斷工具啟用 CPU 分析](../profiling/media/diag-tools-enable-cpu-profiling.png ">diagtoolsenablecpuprofiling")

     當您選擇 [記錄 CPU 分析] 時，Visual Studio 就會開始錄製您的函式以及它們所需的執行時間。 只有在應用程式於中斷點停止時，您才能檢視收集的資料。

8. 按 F5 使應用程式執行至第二個中斷點。

     現在，您擁有在兩個中斷點之間執行的程式碼區域專屬的應用程式效能資料。

     程式碼剖析工具隨即開始準備執行緒資料。 等候它完成。

     ![準備執行緒的診斷工具](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     [CPU 使用量] 工具會在 [CPU Usage (CPU 使用量)] 索引標籤中顯示報告。

     ![診斷工具 CPU 使用量索引標籤](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. 如果您想要選取程式碼更特定的區域進行分析，請在 CPU 時間軸中選取區域 (必須是顯示分析資料的區域)。

     ![選取時間區段的診斷工具](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     此時，您可以開始分析資料。

     > [!TIP]
     >  嘗試找出效能問題時，請採取多項度量。 效能自然會因執行時而異，而且程式碼路徑通常會在第一次執行時變慢，例如載入 Dll、JIT 編譯方法，以及初始化快取。 藉由採取多項度量，您可以更瞭解所顯示度量的範圍和中位數，whichs 可讓您比較第一次與程式碼區域的穩定狀態效能。

## <a name="step-2-analyze-cpu-usage-data"></a>步驟 2：分析 CPU 使用量資料

建議您先檢查 [CPU 使用量] 下方的函式清單、識別執行最多工作的函式，仔細觀察每一項，接著開始分析您的資料。

1. 在函式清單中，檢查執行最多工作的函式。

    ![診斷工具 CPU 使用量函數清單](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > 執行工作最多的函式會優先列出 (不是以呼叫順序列出)。 這可協助您快速找出執行時間最長的函式。

2. 在函式清單中，連按兩下執行大量工作的其中一個應用程式函式。

    當您按兩下函式時，[Caller/Callee (呼叫者/被呼叫者)] 檢視會在左窗格中開啟。

    ![診斷工具的呼叫端/被呼叫端檢視](../profiling/media/diag-tools-caller-callee.png ">diagtoolscallercallee")

    在此檢視中，選取的函式會出現在標題和 [目前的函式] 方塊中 (在此範例中為 GetNumber)。 呼叫目前函式的函式顯示在左邊的 [正在呼叫函式] 下方，而目前函式所呼叫的任何函式會顯示在右邊的 [呼叫的函式] 方塊。 (您可以選取任一個方塊來變更目前的函式。)

    此檢視會顯示總時間 (毫秒) 及完成函式所需時間在整體應用程式執行時間所佔的百分比。
    [函式主體] 也會顯示函式主體所花費的總時間 (和時間百分比)，不包括呼叫的函式和所呼叫函式所花的時間。 (在此範例中，2389 毫秒中的 2367 毫秒花在函式主體，其餘 22 毫秒則花在此函式呼叫的外部程式碼)。

    > [!TIP]
    > [函式主體] 值高可能表示函式本身內有效能瓶頸。

3. 若要查看較概略的檢視 (以呼叫函式的順序顯示)，請從窗格上方的下拉式清單中選取 [呼叫樹狀圖]。

    圖中的每個編號區域與程序中的步驟相關。

    ::: moniker range=">=vs-2019"
    ![診斷工具的呼叫樹狀結構](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![診斷工具的呼叫樹狀結構](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |映像|描述|
    |-|-|
    |![步驟 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU 使用量呼叫樹狀圖中的最上層節點是虛擬節點|
    |![步驟 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|在大部分的應用程式中，停用 [顯示外部程式碼] [](#view-external-code) 選項時，第二層節點是一個含有系統和 Framework 程式碼的 [外部程式碼]  節點，而系統和 Framework 程式碼會啟動和停止應用程式、繪製 UI、控制執行緒排程，以及提供應用程式的其他低階服務。|
    |![步驟 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|第二層節點的子系是第二層系統和 Framework 程式碼所呼叫或建立的使用者程式碼方法和非同步常式。|
    |![步驟4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|某個方法的子節點只包含父系方法呼叫的資料。 停用 [顯示外部程式碼]  時，應用程式方法也可包含 [外部程式碼]  節點。|

    以下是關於資料行值的詳細資訊︰

    - [Total CPU (CPU 總計)] 表示函式及其呼叫的任何函式已完成多少工作。 高 CPU 總計值指向整體耗費最多資源的函式。

    - [Self CPU (自我 CPU)] 表示函式主體中的程式碼已完成多少工作，但會排除其呼叫的函式所完成的工作。 [Self CPU (自我 CPU)] 值高可能表示函式本身內有效能瓶頸。

    - [Modules (模組)] 內含函式的模組名稱，或內含 [External Code (外部程式碼)] 節點中的函式的模組數目。

    ::: moniker range=">=vs-2019"
    若要在呼叫樹狀圖檢視中查看 CPU 使用百分比最高的函式呼叫，請按一下 [展開最忙碌路徑]。

    ![診斷工具的最忙碌路徑](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > 如果您在呼叫樹狀圖中看見被標記為 [中斷] 程式碼或 [無法行進的堆疊] 的程式碼，這表示系統很可能已經卸除 Windows 事件追蹤 (ETW) 事件。 請嘗試再次收集相同的追蹤以解決此問題。

## <a name="view-external-code"></a>檢視外部程式碼

外部程式碼是在系統和架構元件中由您撰寫之程式碼所執行的函式。 外部程式碼包含啟動和停止應用程式、繪製 UI、控制執行緒，以及將其他低階服務提供給應用程式的函式。 在大多數情況下，您對外部程式碼並不感興趣，因此 [CPU 使用量] 工具會將使用者方法的外部函式，收集成一個 [外部程式碼] 節點。

如果您想要檢視外部程式碼的呼叫路徑時，請從 [Filter (篩選)] 檢視清單中選擇 [Show External Code (顯示外部程式碼)]  ，然後選擇 [(Apply) 套用] 。

![選擇 [篩選檢視]，然後選擇 [顯示外部程式碼]。](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

請注意，許多外部程式碼呼叫鏈結都是深度巢狀的，因此 [函式名稱] 資料行的寬度可能會超出所有電腦監視器 (但不含最大的電腦監視器) 的顯示寬度。 發生這種情況時，函式名稱會顯示為 **[...]**。

使用搜尋方塊尋找您所尋找的節點，然後使用水平捲軸檢視資料。

> [!TIP]
> 如果您分析呼叫 Windows 函式的外部程式碼，您應該要確定您有最新的 .*pdb* 檔案。 如果沒有這些檔案，您的報告檢視會列出隱晦且難以了解的 Windows 函式名稱。 如需如何確認您擁有所需檔案的詳細資訊，請參閱 [在偵錯工具中指定符號 ( .pdb) 和原始程式](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔。

## <a name="next-steps"></a>下一步

在本教學課程中，您已了解如何收集並分析 CPU 使用量資料。 如果您已完成[初步認識分析工具](../profiling/profiling-feature-tour.md)，建議您快速查看如何分析應用程式的記憶體使用量。

> [!div class="nextstepaction"]
> [分析 Visual Studio 中的記憶體使用量](../profiling/memory-usage.md)
