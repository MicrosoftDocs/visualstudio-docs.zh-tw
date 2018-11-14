---
title: 在 Visual Studio 中使用虛擬使用者活動圖以進行負載測試
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 19d2a50eba8850b3950e951da58800aed77931ad
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295786"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>逐步解說：使用虛擬使用者活動圖來找出問題

在此逐步解說中，您將了解如何使用「虛擬使用者活動圖」找出執行負載測試之個別虛擬使用者所發生的錯誤。

虛擬使用者活動圖可讓您虛擬化與負載測試相關聯的虛擬使用者活動。 圖表中的每一列都表示個別的虛擬使用者。 虛擬使用者活動圖會顯示每一個虛擬使用者在測試期間的行為。 這樣可讓您藉由查看使用者活動模式、負載模式來找出效能問題、讓失敗或緩慢的測試產生關聯，以及查看其他虛擬使用者活動的要求。 虛擬使用者活動圖只有在負載測試完成執行之後才能使用。

在這個逐步解說中，您將完成下列工作：

-   了解如何使用下列與「虛擬使用者活動圖」相關聯的工具：

    -   使用 [縮放至時間週期] 工具可在圖表上指定您要分析的特定時間週期。

    -   使用 [詳細資料圖例] 面板和 [篩選結果] 面板套用篩選至圖表，以協助找出問題。

-   使用 [虛擬使用者活動圖] 分析特定虛擬使用者所發生的錯誤，並且檢視有問題的錯誤類型詳細資料。

如需詳細資訊，請參閱[在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)。

## <a name="prerequisites"></a>必要條件

-   Visual Studio 企業版

-   完成下列程序：

    -   [記錄和執行 Web 效能測試](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests)。

    -   [建立和執行負載測試](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>開啟在先前逐步解說中建立的 ColorWebApp 方案

### <a name="open-the-solution"></a>開啟方案

1.  啟動 Visual Studio。

2.  開啟包含 *LoadTest1.loadtest* 的 **ColorWebApp** 方案。 此負載測試是執行本主題開頭必要條件章節中所列三個逐步解說的步驟所產生。

     此逐步解說中的其餘步驟假設 Web 應用程式的名稱是 ColorWebApp、Web 效能測試的名稱是 *ColorWebAppTest.webtest*，以及負載測試的名稱是 *LoadTest1.loadtest*。

## <a name="run-the-load-test"></a>執行負載測試

執行負載測試以收集虛擬使用者活動資料。

-   在 [負載測試編輯器] 中，選擇工具列上的 [執行] 按鈕。 LoadTest1 便會開始執行。

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>在虛擬使用者活動圖中找出問題

執行負載測試並且收集虛擬使用者活動資料之後，您可以在 [虛擬使用者活動圖] 中使用 [負載測試分析器] 的 [詳細資料] 檢視，檢視負載測試結果中的資料。 此外，您還可以使用 [虛擬使用者活動圖]，協助您找出負載測試中的效能問題。

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>若要在負載測試結果中使用虛擬使用者活動圖

1.  在負載測試完成執行之後，[負載測試分析器] 中會顯示負載測試結果的 [摘要] 頁面。 選擇工具列上的 [圖形] 按鈕。

     [圖形] 檢視隨即顯示。

2.  在 [頁面回應時間] 圖形上，於其中一個臨界值違規圖示附近按一下滑鼠右鍵，然後選取 [移至使用者詳細資料]。

    > [!NOTE]
    > 您也可以使用 [負載測試編輯器] 工具列中的 [詳細資料] 按鈕，開啟使用者活動圖。 不過，如果您使用 [移至使用者詳細資料] 選項，[虛擬使用者活動圖] 會自動放大您在圖表中以滑鼠右鍵按一下的測試部分。

     在顯示的 [詳細資料] 檢視中，[虛擬使用者活動圖] 的焦點會在發生臨界值違規的時段上。

     在 Y 軸上，水平繪圖表示個別虛擬使用者。 X 軸會顯示負載測試回合的時間線。

3.  在 [虛擬使用者活動圖] 下方的 [縮放至時間週期] 工具中，將左和右滑桿調整到接近臨界值違規圖示的位置。 這會變更 [虛擬使用者活動圖] 中的時間刻度。

4.  在 [詳細資料圖例] 中，選取 [(反白顯示錯誤)] 的核取方塊。 請注意，造成臨界值違規的虛擬使用者會反白顯示。

5.  在 [篩選結果] 面板中，清除 [顯示成功的結果] 和 [HttpError] 核取方塊，但保留選取 [ValidationRuleError] 核取方塊。

     [虛擬使用者活動圖] 只會顯示在 *Red.aspx* 頁面上停留超過 3 秒的虛擬使用者，如在先前逐步解說中設定的閾值違規所指定。

6.  將滑鼠指標停留在代表發生臨界值違規之驗證規則錯誤的虛擬使用者的水平線上。

7.  工具提示隨即出現，其中包含下列資訊：

    -   **使用者 ID**

    -   **案例**

    -   **測試**

    -   **結果**

    -   **Network**

    -   **開始時間**

    -   **持續期間**

    -   **代理程式**

    -   **測試記錄**

8.  請注意，[測試記錄] 是連結。 選擇 [測試記錄] 連結。

9. 與記錄相關聯的 ColorWebTest Web 效能測試會在 [Web 效能測試結果檢視器] 中開啟。 這樣您就可以找出發生臨界值違規的位置。

     您可以使用 [詳細資料圖例] 和 [篩選結果] 這兩個面版中的各項設定，幫助您找出效能問題和負載測試中的錯誤。 嘗試使用這些設定和 [縮放至時間週期] 工具，查看 [虛擬使用者活動圖] 如何呈現虛擬使用者資料。

## <a name="see-also"></a>另請參閱

- [在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [測試控制器和測試代理程式](configure-test-agents-and-controllers-for-load-tests.md)
- [如何：建立分散式負載測試的測試設定](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)
- [使用測試設定收集診斷資訊](../test/collect-diagnostic-information-using-test-settings.md)
