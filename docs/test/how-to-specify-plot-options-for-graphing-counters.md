---
title: Visual Studio 中用於負載測試的圖形計數器繪圖選項
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5df33a8cf05e4ad73b1643e2948392e49a32356e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382317"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>如何：指定圖表計數器的繪圖選項

[繪圖選項] 對話方塊可讓您變更圖形上所繪製計數器的色彩和線條樣式。 您也可以將範圍固定為特定值，或將範圍設定為根據取樣資料自動調整。

![[繪圖選項] 對話方塊](../test/media/ltest_plotoptions.png)

## <a name="to-specify-plotting-options-for-graphs"></a>若要指定圖形的繪圖選項

1.  在 [負載測試分析器] 中，選擇工具列上的 [圖表]。

     這會在 [圖表] 檢視中顯示負載測試結果。

2.  在圖例或圖表中，以滑鼠右鍵按一下您要變更繪圖選項之效能計數器的資料列或目前的繪製線條，然後選取 [繪圖選項]。

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

- [在圖表檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)
- [如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)
