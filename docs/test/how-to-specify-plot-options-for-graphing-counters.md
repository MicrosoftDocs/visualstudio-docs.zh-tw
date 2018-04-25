---
title: Visual Studio 中用於負載測試的圖形計數器繪圖選項 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 5c52aefb731fdb1c858819d1c005d27000ad840e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>如何：指定圖形計數器的繪圖選項

[繪圖選項] 對話方塊可讓您變更圖形上所繪製計數器的色彩和線條樣式。 您也可以將範圍固定為特定值，或將範圍設定為根據取樣資料自動調整。

![[繪圖選項] 對話方塊](../test/media/ltest_plotoptions.png "LTest_PlotOptions")

## <a name="to-specify-plotting-options-for-graphs"></a>若要指定圖形的繪圖選項

1.  在 [負載測試分析器] 中，選擇 [負載測試] 工具列上的 [圖形]。

     這樣會在 [圖形] 檢視中顯示負載測試結果。

2.  在圖例或圖形中，以滑鼠右鍵按一下您想要變更繪圖選項之效能計數器的資料列或目前的繪製線條，然後選取 [繪圖選項]。

     [繪圖選項] 對話方塊隨即顯示。

3.  使用 [色彩] 下拉式清單，並選取您想要用來繪製效能計數器的色彩。

4.  使用 [樣式] 下拉式清單，並選取您想要用來繪製效能計數器的樣式。

5.  執行下列任一步驟：

     選取 [自動調整範圍] (預設值)

     \-或-

     清除 [自動調整範圍] 並使用 [範圍] 下拉式清單，指定您想要用來繪製效能計數器的範圍。

6.  選擇 [確定] 。

     您已變更其選項的效能計數器就會使用指定的變更顯示在圖形中。

## <a name="see-also"></a>另請參閱

- [在圖形檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)
- [如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [在圖形檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)