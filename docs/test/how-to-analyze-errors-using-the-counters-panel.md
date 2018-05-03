---
title: 在 Visual Studio 中使用計數器面板來分析負載測試錯誤
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e37b39d504059491318913f6eb1345d73ef3074b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>如何：使用計數器面板來分析錯誤

當負載測試正在執行，或者您正在分析負載測試結果時，[計數器] 面板就會顯示在 [負載測試分析器] 的 [圖形] 檢視和 [資料表] 檢視中。 如需詳細資訊，請參閱[在圖形檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)、[在資料表檢視中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)和[如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)。

 [計數器] 面板中的 [錯誤] 節點包含負載測試期間偵測到的所有錯誤。 [錯誤] 節點包含不同的錯誤種類專屬的數個子分類錯誤節點。 例如，[例外狀況] 和 [HTTP 錯誤]。

 ![計數器面板的錯誤節點](../test/media/ltest_errornode.png "LTest_ErrorNode")

## <a name="to-analyze-errors-in-the-counters-panel"></a>在計數器面板中分析錯誤

1.  在負載測試完成或是載入測試結果之後，於 [負載測試分析器] 的工具列中選擇 [圖形] 或 [資料表]。

     [計數器] 面板就會顯示在 [圖形] 檢視或 [資料表] 檢視中。

2.  如果看不見 [計數器] 面板，請選擇工具列上的 [顯示計數器面板]。

3.  展開 [錯誤]，並且選取錯誤分類或您要分析的錯誤子分類。

4.  以滑鼠右鍵按一下錯誤，然後選取下列其中一個選項：

    -   **在圖形上顯示計數器**：在 [圖形] 檢視中，錯誤會新增至選取的圖形並反白顯示。 如需詳細資訊，請參閱[如何：在圖形上新增和刪除計數器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)。

    -   **在圖例上顯示計數器**：錯誤會新增至圖例中並顯示為已選取狀態。 如需詳細資訊，請參閱[使用圖形檢視圖例來分析負載測試](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)。

    -   **新增圖形**：

    1.  [輸入圖形名稱] 對話方塊隨即顯示。

    2.  在 [圖形名稱] 文字方塊中，輸入新圖形的名稱，然後選擇 [確定]。

    3.  (選擇性) 再次以滑鼠右鍵按一下錯誤，然後選取 [在圖形上顯示計數器]。

         如需詳細資訊，請參閱[如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)。

5.  (選擇性) 如果您要在已完成的負載測試結果中分析錯誤，請考慮在 [圖形] 中時使用縮放功能。 如需詳細資訊，請參閱[如何：放大圖形中的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)。

    > [!TIP]
    > 如果在負載測試回合期間偵測到任何錯誤，名為「錯誤」(包括找到的數目) 的連結就會出現在 [負載測試分析器] 狀態列中。 選擇此連結，即可在 [資料表] 檢視的 [錯誤] 資料表中顯示所有錯誤。

## <a name="see-also"></a>另請參閱

- [使用圖形檢視和資料表檢視中的計數器面板](../test/counters-panel-in-load-test-analyzer.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)