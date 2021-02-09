---
title: 放大負載測試結果圖形
description: 瞭解如何使用縮放列來放大及滾動至圖形的某個區域，以更詳細的方式檢查負載測試回合期間所產生的資料。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: af780af58e3efa2aff7dc58971bfbbb881967c40
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879536"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>如何：放大負載測試結果圖表中的某個區域

完成負載測試後，可以使用縮放列來放大及捲動到圖形的某個區域。 藉由圖形放大，您可以更為仔細地檢查負載測試回合期間收集到的資料。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

只有在分析完成的負載測試結果時才能使用放大，在觀察執行中測試的結果時則無法放大。

只有當您以縮放模式檢視負載測試結果時，縮放控制項才會顯示在 [負載測試分析器] 中。 當負載測試已完成時或載入先前執行的負載測試時，會在 [圖形] 檢視中建立縮放模式。 使用工具列上的 [顯示縮放控制]，即可在圖表上顯示或隱藏縮放控制項。

您可以調整 **水平 X 軸縮放**，以便在負載測試期間分析特定時間週期。 您可以調整 **垂直 Y 軸縮放**，以便分析圖表中計數器的特定值範圍。

**水平時間軸** 和 **垂直值範圍** 縮放控制項都可以透過滑鼠來調整。 **水平時間軸控制項** 也可以透過左右方向鍵來調整。 使用方向鍵調整縮放控制項，每次能以 1 個取樣間隔為單位調整視窗範圍。 使用 **Shift** 和方向鍵會以 10 個取樣間隔為單位來調整。

若要使用方向鍵調整縮放控制項，請先使用 **Tab** 鍵將焦點設在縮放控制項上。 當左滑桿有焦點時，方向鍵會以 1 個間隔為單位向左或向右移動縮放視窗的開始界限。 當焦點在中央滑桿上時，可使用方向鍵以 1 個取樣間隔為單位向左或向右捲動縮放視窗，而不會變更縮放視窗的大小。 最後，右滑桿會移動，以 1 個取樣間隔為單位延伸或縮短縮放視窗結尾的範圍。

若要恢復水平和垂直縮放控制以顯示完整的時間軸和值範圍，您可以使用圖形上快顯功能表中的 [水平縮小] 選項、[垂直縮小] 選項或 [縮小兩者] 選項。

> [!TIP]
> 您可以使用工具列中的 [同步水平縮放控制]，開啟或關閉自動水平縮放同步處理。 當同步處理開啟時，套用至某個圖表上的任何縮放也會套用至 [圖表] 檢視上的任何其他圖表。

![圖形檢視縮放控制](../test/media/ltest_zoomcontrol.png)

在上圖中，已放大 **待測系統** 圖表來調查閾值問題。 臨界值違規已透過工具列之 [圖形選項] 下拉式清單中的 [在圖形上顯示臨界值違規] 來啟用。

如需詳細資訊，請參閱 [在圖形視圖中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)。

## <a name="display-graphs"></a>顯示圖表

在您藉由縮放和捲動來變更圖形顯示前，請遵循下列程序顯示圖形。

若要顯示圖形：

1. 執行負載測試，直到完成。

2. 負載測試回合結束時，在詢問是否要檢視來自負載測試結果存放區之結果的對話方塊中，選擇 [是]。

     \- 或 -

     檢視先前執行的負載測試的詳細資料。 如需詳細資訊，請參閱 [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)。

3. 如果沒有顯示圖形，請選擇 [圖形]。

4. 如果沒有顯示縮放列，請選擇 [顯示縮放控制]。

     每個圖形都有兩個縮放列。 控制垂直縮放的縮放列會出現在圖形左方。 控制水平縮放的縮放列會出現在圖形下方。

     每個縮放列都有兩個控點。 控點是縮放列兩端的矩形區域。

## <a name="zoom-and-scroll"></a>縮放和捲動

顯示多個圖形時，您可以讓它們保持同步，這樣它們可以顯示負載測試回合的相同部分。

### <a name="to-synchronize-zooming-and-scrolling"></a>若要同步縮放和捲動

1. 在 [ **負載測試分析器**] 上，選擇 [ **同步水準縮放控制**]。

     在選取 [同步水平縮放控制] 按鈕的情況下，對個別圖表時間刻度的縮放和捲動，也會縮放和捲動其他圖表的時間刻度。

2. 再次選擇 [同步水平縮放控制]。

     在沒有選取 [同步水平縮放控制] 按鈕的情況下，對個別圖表時間刻度的縮放和捲動，只會影響到該圖表。

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>若要縮放和捲動圖形的區域

1. 在圖形下的縮放列上，將左方控點拖曳到右邊。

     這樣會放大測試回合後面的部分。 同樣地，將右方控點拖曳到左邊會放大測試回合前面的部分。

2. 若要放大特定區域，將兩端控點向圖形中央滑動。

     這兩個控點彼此越接近，就放得越大，顯示的負載測試區段也就越短、越精細。

     選擇縮放列的中央部分，再拖曳以捲動到負載測試的特定點。

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>若要藉由選擇和拖曳來縮放圖形的區域

1. 在縮放區域的一端選擇圖形。

2. 拖曳滑鼠指標到縮放區域的另一端。

3. 放開滑鼠按鈕。

    這樣會放大您藉由選擇和拖曳所定義的區域。

   下列程序描述如何在不需要調整縮放列端點的情況下快速縮小。

### <a name="to-zoom-out"></a>若要縮小

1. 以滑鼠右鍵按一下放大的圖形。

2. 在捷徑功能表上，選取 [水平縮小]。

     這樣會縮小圖形，顯示負載測試回合的整個持續期間。

## <a name="see-also"></a>另請參閱

- [在圖表檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [如何：在圖形上新增和刪除計數器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
