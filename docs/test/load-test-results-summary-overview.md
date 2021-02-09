---
title: 負載測試結果摘要概觀
description: 瞭解如何查看負載測試摘要。 負載測試摘要以精簡易讀的格式提供主要的結果。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ac7fa64b143127d8efe030a94242b237ff9e0d49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887714"
---
# <a name="load-test-results-summary-overview"></a>負載測試結果摘要概觀

執行負載測試之後，您可以檢視負載測試摘要，快速了解測試的結果。 負載測試摘要以精簡易讀的格式提供主要的結果。 您也可以列印負載測試摘要， 以方便您和專案關係人一起討論測試的結果。 當您從先前執行的負載測試開啟負載測試結果時，負載測試摘要也是預設檢視。 如需詳細資訊，請參閱 [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)。

![摘要檢視](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>負載測試摘要

負載測試摘要分成數個區段。 初始區段顯示在摘要最上方，而且將一直維持顯示狀態。 當您檢視負載測試摘要時，下列項目將會顯示在最前面：

- 測試回合資訊

- 整體結果

- 基本統計資料: 前 5 名最慢的頁面

- 基本統計資料: 前 5 名最慢的測試

- 基本統計資料: 前 5 名最慢的 SQL 作業

    > [!NOTE]
    > 只有當負載測試啟用了 SQL 追蹤功能時，才會顯示 SQL 作業區段。

結尾區段顯示在摘要的結尾處；您可以摺疊這些區段以節省空間。 下列項目將顯示在負載測試摘要的結尾處：

- 測試結果

- 頁面結果

- 異動結果

- 待測系統資源

- 控制器和代理程式資源

- Errors

## <a name="test-run-information"></a>測試回合資訊

測試回合資訊區段包含測試回合的一般資訊，包括測試的名稱、開始和結束時間，以及執行測試的控制器。 這個區段也包含您在執行負載測試時加入的有關回合的選擇性 (Optional) 描述。

## <a name="overall-results"></a>整體結果

整體結果區段包含測試的摘要結果，包括每秒的要求數、已失敗的要求總數、平均回應時間，以及平均頁面時間。

## <a name="key-statistic-top-5-slowest-pages"></a>基本統計資料：前 5 名最慢的頁面

最慢的頁面區段包含負載測試中前 5 名最慢的頁面， 並顯示每個頁面的 URL 和平均頁面載入時間。 這些頁面是依遞減順序列出。 您可以選擇頁面的 URL 開啟 [頁面] 資料表，並查看該頁面的其他詳細資料。 如需詳細資訊，請參閱 [如何：查看網頁回應](../test/how-to-view-web-page-response-time-in-a-load-test.md)。

[95% 頁面時間 (秒)] 的百分位數會報告 95% 頁面的完成時間都不超過這段時間 (以秒為單位)。

## <a name="key-statistic-top-5-slowest-tests"></a>基本統計資料：前 5 名最慢的測試

最慢的測試區段包含負載測試中前 5 名最慢的測試， 並顯示每一項測試的測試名稱和平均測試時間。 這些測試是依遞減順序列出。 您可以選擇測試的名稱開啟 [測試] 資料表，並查看該測試的其他詳細資料。 如需詳細資訊，請參閱在 [資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

[95% 測試時間 (秒)] 的百分位數會報告 95% 測試的完成時間都不超過這段時間 (以秒為單位)。

## <a name="key-statistic-top-5-slowest-sql-operations"></a>基本統計資料：前 5 名最慢的 SQL 作業

如果在負載測試中啟用了 SQL 追蹤，最慢的查詢區段就會包含負載測試中前 5 名最慢的查詢， 並顯示每一項測試的作業名稱和持續時間。 持續時間的顯示單位是微秒 (SQL Server 2005) 或毫秒 (SQL Server 2000 和更早版本)。 這些測試是按照持續時間依遞減順序列。 您可以選擇作業的名稱開啟 [SQL 追蹤] 資料表，並查看該項作業的其他詳細資料。 如需詳細資訊，請參閱 [SQL 追蹤資料表](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table)。

## <a name="test-results"></a>測試結果

測試結果區段包含負載測試中所有測試和情節的清單， 並顯示測試的名稱、情節、執行次數、失敗次數和平均測試時間。 您可以選擇測試的名稱開啟 [測試] 資料表，並查看該測試的其他詳細資料。 如需詳細資訊，請參閱在 [資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

> [!NOTE]
> 選擇區段標題左側的箭號，就可以摺疊或展開此區段。

## <a name="page-results"></a>頁面結果

頁面結果區段包含負載測試中所有網頁的清單， 並顯示 URL、情節、測試的名稱、平均頁面時間和計數。 您可以選擇頁面的 URL 開啟 [頁面] 資料表，並查看該頁面的其他詳細資料。 如需詳細資訊，請參閱 [如何：查看網頁回應](../test/how-to-view-web-page-response-time-in-a-load-test.md)。

> [!NOTE]
> 選擇區段標題左側的箭號，就可以摺疊或展開此區段。

## <a name="transaction-results"></a>異動結果

異動結果區段包含負載測試中所有異動的清單， 並顯示異動的名稱、情節、測試、回應時間、耗用時間和計數。 您可以選擇異動的名稱開啟 [異動] 資料表，並查看該異動的其他詳細資料。 如需詳細資訊，請參閱在 [資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

> [!NOTE]
> 選擇區段標題左側的箭號，就可以摺疊或展開此區段。

這些百分位數會報告下列異動資訊：

- 90% 的總交易已在不到秒的 \<time> 時間內完成。

- 95% 的總交易已在不到秒的 \<time> 時間內完成。

## <a name="system-under-test-resources"></a>待測系統資源

待測系統資源區段包含一份電腦清單，其中列出正在產生負載的一組目標電腦， 包括您向其收集代理程式或控制器以外之計數器集合的任何電腦。 此區段所顯示的資訊包括電腦名稱、% 處理器時間和可用記憶體。 您可以選擇電腦名稱開啟 [待測系統] 圖，並查看一段時間的資源使用狀況。 如需詳細資訊，請參閱 [在圖形視圖中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)。

> [!NOTE]
> 選擇區段標題左側的箭號，就可以摺疊或展開此區段。

## <a name="controller-and-agent-resources"></a>控制器和代理程式資源

控制器和代理程式資源區段包含用來執行測試的電腦清單。 此區段所顯示的資訊包括電腦名稱、% 處理器時間和可用記憶體。 您可以選擇電腦名稱開啟 [控制器和代理程式] 圖，並查看一段時間的資源使用狀況。 如需詳細資訊，請參閱 [在圖形視圖中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)。

> [!NOTE]
> 選擇區段標題左側的箭號，就可以摺疊或展開此區段。

## <a name="errors"></a>Errors

錯誤區段包含負載測試期間發生之所有錯誤的清單， 並顯示錯誤的類型及子類型、計數和最後一則訊息。 您可以選擇錯誤開啟 [錯誤] 資料表，並查看該錯誤的其他詳細資料。 如需詳細資訊，請參閱在 [資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

> [!NOTE]
> 選擇區段標題左側的箭號，就可以摺疊或展開此區段。

## <a name="print-a-summary"></a>列印摘要

在負載測試摘要的捷徑功能表中選擇 [列印]，就可以列印摘要。 如果想先預覽列印，請在摘要的捷徑功能表上選擇 [預覽列印]。 您也可以直接從預覽畫面列印摘要。

## <a name="see-also"></a>另請參閱

- [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
