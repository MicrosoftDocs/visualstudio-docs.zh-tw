---
title: 分析負載測試的臨界值規則違規
description: 瞭解如何查看您所設定的臨界值規則違規，讓您可以分析違規。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49fe5893254083dd83551ef5f43fffcc295a992a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442699"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>使用負載測試分析器來分析負載測試中的臨界值規則違規

臨界值規則與特定的效能計數器有關，而違規指的是效能計數器超過或未達設定值。 當您執行負載測試時，可以針對事先設定的臨界值規則分析所發生的違規。

如果發生違規，**負載測試分析器** 的狀態列就會出現 [臨界值違規] 超連結，並指出發生的違規數量。 您可以選擇超連結顯示臨界值違規資料表。 您也可以在 [計數器] 視窗和圖形上檢視臨界值違規。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>在資料表中檢視臨界值違規

臨界值違規資料表會顯示最前面的 1,000 個違規。 下表包含這些資料行：

|資料行|描述|預設為可見|
|-|-|-|
|時間|負載測試期間發生違規的時間。|是|
|電腦|發生違規之測試中的電腦名稱。 **注意：** 當您在 Rig 上執行負載測試時，這很重要。|是|
|類別|發生違規之效能計數器的分類。|是|
|計數器|發生違規之效能計數器的名稱。|是|
|執行個體|發生違規的效能計數器執行個體。|是|
|訊息|描述臨界值違規的訊息。 例如，**值 5 超過 0 的關鍵臨界值**。|是|

> [!NOTE]
> 選擇資料行標頭即可排序資料表。

如需詳細資訊，請參閱在 [資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

## <a name="view-threshold-violations-in-the-counters-panel"></a>在計數器面板中檢視臨界值違規

您可以在 [計數器] 面板中，於列出負載測試之效能計數器的樹狀目錄中，檢閱臨界值違規。 [計數器] 面板中的圖示會傳達臨界值違規。 其圖示可以是下列其中之一：

其圖示可以是下列其中之一：

![無臨界值違規](../test/media/icon_ltest_1.gif) 無臨界值違規。

![最新間隔期間的嚴重臨界值違規](../test/media/icon_ltest_2.gif) 在最後一個間隔中發生了嚴重臨界值違規。

![預先間隔期間的嚴重臨界值違規](../test/media/icon_ltest_3.gif) 在前一個間隔中發生了嚴重臨界值違規。

![最新間隔期間的警告臨界值違規](../test/media/icon_ltest_4.gif) 在最後一個間隔中發生了警告臨界值違規。

![預先間隔期間的警告臨界值違規](../test/media/icon_ltest_5.gif) 在前一個間隔中發生了警告臨界值違規。

您也可以選擇在圖形上顯示臨界值違規。 臨界值圖示會出現在圖形上發生臨界值違規的資料點旁。

在計數器樹狀目錄中，臨界值違規的圖示是從特定的計數器節點傳送過來的，最深可達根節點。 這會提醒您在樹狀目錄上可能看不到 (因為樹狀目錄未展開) 之計數器的違規。

## <a name="view-threshold-violations-on-the-graph"></a>在圖形上檢視臨界值違規

您可以在圖形上檢視臨界值違規。 圖示與 [計數器] 面板類似，會在圖形上傳達臨界值違規。 在圖形上之資料旁邊出現的圖示，指出發生臨界值違規的位置。 如果臨界值違規是在圖形上未出現的計數器上發生，您可以將該計數器從 [計數器] 面板拖曳至圖形上，藉此將它新增至圖形。

如需詳細資訊，請參閱 [在圖形視圖中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)。

## <a name="see-also"></a>另請參閱

- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [在資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
