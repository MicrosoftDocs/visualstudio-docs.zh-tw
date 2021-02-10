---
title: '分析負載測試結果-圖形視圖 (負載測試分析器) '
description: 瞭解如何將測試結果顯示為圖形。 每個圖表都會顯示在一個面板中，並在下拉式清單中顯示圖形名稱。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: cbd15d57090f2248cdd97eba1898e363cc2d21b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948071"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>在負載測試分析器的圖形檢視中分析負載測試結果

負載測試的結果會顯示成數個不同窗格中的資料。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

若要將測試結果顯示為圖形，請選擇 [**負載測試**] 工具列上的 [**圖形**]。 在窗格中會顯示每個獨立的圖形，窗格頂端的下拉式清單會顯示圖形名稱。 若要在窗格中顯示不同的圖形，請從清單選擇不同的圖形名稱。

同時最多可以顯示四個圖形。 藉由使用 [面板配置] 工具列按鈕，可以在不同面板配置間切換。

有提供數種內建圖形。 您可以直接使用內建圖形或是自訂這些圖形。 除此之外，您也可以建立自己的圖形。 如需詳細資訊，請參閱 [如何：在圖形上新增和刪除計數器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) 和 how [to：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)。

## <a name="built-in-graphs"></a>內建圖形

下列表格列出可用於分析負載測試結果的內建圖形。

|圖形名稱|Description|
|-|-|
|關鍵指標|用於描述測試效能基本層面的計數器，例如使用者負載、輸送量和回應時間。|
|測試回應時間|執行測試所需時間量的資料。|
|頁面回應時間|負載測試期間所存取 Web 頁面的平均回應時間。|
|待測系統|應用程式要進行測試回合的電腦資訊。 這些資訊包含記憶體使用量、處理器、實體磁碟和處理序的相關資料。<br /><br /> 根據預設，只會收集 Available Mbytes 和 Processor Time 計數器。|
|控制器和代理程式|執行負載測試的電腦資訊。 這些資訊包含記憶體使用量、處理器、實體磁碟和處理序的相關資料。<br /><br /> 根據預設，只會收集 Available Mbytes 和 Processor Time 計數器。|
|異動回應時間|負載測試期間所發生異動的平均回應時間。|

您可以在執行階段或執行測試之後，在圖形上顯示不同的計數器。

> [!NOTE]
> 自動產生的回應時間圖形中僅能加入回應時間效能計數器。

計數器資訊將會在圖形和圖形底下的圖例中出現。 也可以放大圖形中的某個區段。 如需詳細資訊，請參閱 [如何：放大圖形的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)。

## <a name="counters-displayed-in-graphs"></a>圖形中顯示的計數器

圖形會顯示「計數器」。 計數器代表負載測試期間收集到的資料，例如每秒測試數或平均測試時間。 如需有關計數器的詳細資訊，請參閱 [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)。

在圖形中顯示的計數器圖例，會顯示數欄有關負載測試回合的有用資料。 若要關閉圖形中任何資料的顯示，請清除圖例中，位於該列內的核取方塊。

圖例會包含下列欄位：

|計數器|計數器的名稱|
|-|-|
|執行個體|計數器執行個體的名稱。|
|類別|計數器分類的名稱。|
|電腦|要收集計數器的電腦名稱。|
|Color|圖形中線條的色彩。|
|範圍|表示對於該計數器，圖形上的 100 所表示的數目。 舉例來說，對上限值為 10,000 的範圍而言，圖形頂端的 100 標籤即代表 10,000。|
|Min|表示計數器的最小值 (以毫秒為單位)。|
|最大值|表示計數器的最大值 (以毫秒為單位)。|
|平均|表示計數器的平均值 (以毫秒為單位)。|
|最後一個|顯示最近取樣間隔期間的計數器值 (以毫秒為單位)。|

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-|
|**使用圖例自訂圖形：**[圖形] 檢視圖例會顯示每個與圖形建立關聯之效能計數器的資訊。 您可以使用圖例來移除效能計數器、反白顯示圖形中的效能計數器，以及自訂繪圖選項。|-   [使用圖表視圖圖例來分析負載測試](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**在圖形上顯示計數器：** 藉由在圖形上置放計數器，您可以將各種資料新增至負載測試結果圖形。|-   [如何：在圖形上新增和刪除計數器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**放大圖形：** 完成負載測試後，可以使用縮放列來放大及捲動到圖形的某個區域。 藉由圖形放大，您可以更為仔細地檢查負載測試回合期間收集到的資料。|-   [如何：放大圖形中的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**並排顯示圖形：** 您可以使用數種模式排列負載測試結果圖形。 最多可以並排顯示四個圖形。||
|**建立自訂圖形：** 您可以設計用來顯示有關負載測試結果的特定資訊的圖形。 藉由指定圖形要顯示的負載測試計數器，即可以設計自訂圖形。|-   [如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**匯出圖形中的效能計數器資料：** 您可以 **使用 [** **負載測試分析器**] 工具列上的 [將 **圖形資料匯出至 Excel** ] 按鈕，將圖形資料匯出至 Microsoft excel。||

## <a name="related-tasks"></a>相關工作

[在資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)

[分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>另請參閱

- [如何：在圖形上新增和刪除計數器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [如何：放大圖形中的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
