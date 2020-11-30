---
title: 使用圖形檢視圖例來分析負載測試
description: 深入瞭解 [負載測試分析器] 的 [圖形] 窗格，其中包含的 [圖例] 面板會顯示所選圖表的效能計數器資訊。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25200b691e0bebf2e3bd1c6252efb371ed9caeb2
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330065"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>使用圖表檢視圖例來分析負載測試

[負載測試分析器] 的 [圖形] 檢視包含圖例面板，其中顯示每個與目前選取圖形相關聯之效能計數器的資訊。

![圖形檢視圖例](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

下列資訊都包含在此圖例中：

- **在圖形上顯示：** 您可以使用這些核取方塊來指定是否要在圖形上針對特定計數器 (例如 **User load** 或 **Errors/Sec**) 繪製線條。 如果您想要在圖形上繪製線條，請選取核取方塊。 若要從圖形中移除繪圖線條，請清除核取方塊。 移除繪圖線條時，計數器的統計資料會繼續顯示在圖例中。

- **範圍：** 這個資料行會顯示效能計數器的 Y 軸範圍。 根據預設，這個值會在樣本資料範圍變更時自動調整。 自動調整的範圍一定是 10 的下一個次方 (超過最大值)，包括十的負數次方。 圖形可以包含各種計數器，而且每個計數器各有不同的範圍。 因此，Y 軸不會標示任何特定範圍，不過卻會標示 0-100 的值，代表每個計數器總範圍的百分比。 例如，若為範圍是 1000 的計數器，Y 軸上的資料點 60 就會對應至計數器的值 600。

    > [!NOTE]
    > 您可以將範圍鎖定為特定值，藉以關閉自動範圍值調整。 鎖定範圍時，任何超過此範圍的值都會顯示為您在圖形頂端指定的最大值。 請使用 [繪圖選項] 對話方塊，將範圍鎖定為特定值。

- **計數器：** 四個名為 [計數器]、[執行個體]、[分類] 和 [電腦] 的資料行可唯一識別效能計數器。

- **色彩：**[色彩] 資料行會顯示效能計數器之繪製線條的色彩和線條樣式。 請使用 [繪圖選項] 對話方塊來變更圖形上效能計數器的色彩或線條樣式。 您可以從圖例的捷徑功能表存取 [繪圖選項] 對話方塊。

- **統計資料：**[最小值]、[最大值]、[平均值] 和 [最後一筆] 資料行會顯示效能計數器的個別統計資料。 這些值會對應至顯示於圖形可見區域上的資料。 例如，如果您放大某個回合的區域，圖例統計資料就只會反映放大區域的值。 [最後一筆] 資料行是針對上次完成的取樣間隔，效能計數器所呈現的值。

    > [!NOTE]
    > 當負載測試正在執行時，[最後一筆] 資料行只會顯示在 [負載測試分析器] 的圖例中。

     如需詳細資訊，請參閱 [如何：放大圖形的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)。

在圖例中選取項目就會進行下列作業：

- 允許從圖例和圖形中移除項目。 請以滑鼠右鍵按一下項目，然後選取 [刪除] 或按 **Delete** 鍵。

- 反白顯示圖形上的繪製線條。

- 讓資料格顯示所選項目的資料。

- 讓您存取計數器的 [繪圖選項] 對話方塊。

> [!TIP]
> 您可以使用 [負載測試分析器] 工具列中的 [圖表選項] 下拉按鈕，然後選取 [顯示圖例]，以便顯示或隱藏與圖表檢視建立關聯的 [圖例] 面板。

## <a name="see-also"></a>另請參閱

- [如何：放大圖形中的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [在圖表檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)
