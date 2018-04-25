---
title: Visual Studio 中負載測試的臨界值違規 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, threshold violations
ms.assetid: 0126d7b7-0538-4ea9-9046-6556654b3b9d
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6acb9eec16107134dc03765da82008a01b599e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-analyze-threshold-violations-using-the-counters-panel-in-load-test-analyzer"></a>如何：使用負載測試分析器中的計數器面板來分析臨界值違規

當負載測試正在執行，或者您正在分析負載測試結果時，[計數器] 面板就會顯示在 [負載測試分析器] 的 [圖形] 檢視和 [資料表] 檢視中。 請參閱[在圖形檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)、[在資料表檢視中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)和[如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)。

 臨界值違規會與特定的效能計數器相關聯，並且表示效能計數器超過或未達設定的臨界值。 [計數器] 面板中的圖示會傳達臨界值違規。

 ![計數器面板的電腦節點](../test/media/ltest_compnode.png "LTest_CompNode")

 臨界值違規的圖示會從失敗計數器所在的樹狀目錄節點傳播至根目錄。 此圖示會提醒使用者注意在樹狀目錄上可能看不到之計數器的違規，因為樹狀目錄未展開。 您可以在上圖中 [計數器] 面板的 [電腦] 節點中查看此圖示的範例。

 其圖示可以是下列其中之一：

 ![無臨界值違規](../test/media/icon_ltest_1.gif "Icon_LTest_1") 無臨界值違規。

 ![最後一個間隔中的嚴重臨界值違規](../test/media/icon_ltest_2.gif "Icon_LTest_2") 在最後一個間隔中發生了嚴重臨界值違規。

 ![前一個間隔中的嚴重臨界值違規](../test/media/icon_ltest_3.gif "Icon_LTest_3") 在前一個間隔中發生了嚴重臨界值違規。

 ![最後一個間隔中的警告臨界值違規](../test/media/icon_ltest_4.gif "Icon_LTest_4") 在最後一個間隔中發生了警告臨界值違規。

 ![前一個間隔中的警告臨界值違規](../test/media/icon_ltest_5.gif "Icon_LTest_5") 在前一個間隔中發生了警告臨界值違規。

## <a name="to-analyze-threshold-violations-in-the-counters-panel"></a>若要在計數器面板中分析臨界值違規

1.  在負載測試完成或是載入測試結果之後，於 [負載測試分析器] 的工具列中選擇 [圖形] 或 [資料表]。

     [計數器] 面板會在 [圖形] 檢視或 [資料表] 檢視中顯示。

2.  如果看不見 [計數器] 面板，請選擇工具列上的 [顯示計數器面板]。

     任何包含臨界值違規的節點都將含有上列其中一個圖示。

3.  展開包含臨界值圖示的節點 (例如 [電腦] 節點)，如上圖「[計數器] 面板中發生臨界值違規的 [電腦] 節點」所示。 繼續展開節點，直到您到達發生臨界值違規的效能計數器為止。 例如，上圖顯示 [Microsoft 虛擬機器失敗匯流排網路介面卡] 的失敗執行個體。

4.  (選擇性) 以滑鼠右鍵按一下發生臨界值違規的效能計數器，然後選取下列其中一個選項：

    -   **在圖形上顯示計數器**：在 [圖形] 檢視中，效能計數器會新增至選取的圖形並反白顯示。 如需詳細資訊，請參閱[如何：在圖形上新增和刪除計數器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)。

        > [!NOTE]
        > 臨界值違規圖示也可以顯示在 [圖形] 檢視的圖形上。 臨界值圖示會出現在圖形上發生臨界值違規的資料點旁。 若要這樣做，請選擇工具列上的 [顯示圖例] 下拉式清單，然後選取 [在圖形上顯示臨界值違規]。

    -   **在圖例上顯示計數器**：效能計數器會新增至圖例並呈現選取狀態。 如需詳細資訊，請參閱[使用圖形檢視圖例來分析負載測試](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)。

    -   **新增圖形**：

    1.  [輸入圖形名稱] 對話方塊隨即顯示。

    2.  在 [圖形名稱] 文字方塊中，鍵入新圖形的名稱，然後選擇 [確定]。

    3.  (選擇性) 再次以滑鼠右鍵按一下效能計數器，然後選取 [在圖形上顯示計數器]。

         如需詳細資訊，請參閱[如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)。

5.  (選擇性) 如果您要在已完成的負載測試結果中分析臨界值違規，請考慮使用 [圖形] 檢視中的縮放功能。 如需詳細資訊，請參閱[如何：放大圖形中的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)。

    > [!TIP]
    > 如果在負載測試回合期間偵測到任何臨界值違規，名為「臨界值違規」(包括違規數目) 的連結就會出現在 [負載測試分析器] 狀態列中。 您可以選擇此連結，在 [資料表] 檢視的 [臨界值] 資料表中顯示所有臨界值違規。

## <a name="see-also"></a>另請參閱

- [使用圖形檢視和資料表檢視中的計數器面板](../test/counters-panel-in-load-test-analyzer.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)