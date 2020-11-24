---
title: 分析負載測試結果與錯誤
description: 瞭解如何顯示窗格，以提供不同的方式來分析負載測試回合的結果，例如隨時間或詳細資料表的圖形。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7787b3b0afaed0bc3592b458646b97151e309905
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442504"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>在負載測試分析器的資料表檢視中分析負載測試結果和錯誤

當您檢視負載測試回合的結果時，您可以顯示不同窗格以提供不同的資料分析方法。 您可以用圖形方式檢視資料，觀察資料在時間過程中如何改變，或者可以用詳細資料表的方式檢視資料。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

若要切換到資料表視圖，請選擇 [**負載測試**] 工具列上的 [**資料表]** 。 若要在不同資料表之間切換，請使用資料表方格上工具列的 [資料表] 下拉式清單。 在資料表檢視中，您一次最多可以檢視四份資料表。 如需詳細資訊，請參閱本主題中的[並排顯示負載測試資料表](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables)。

在效能計數器資料表中顯示的大部分數值是整個負載測試回合的累加。 名為 [最後一筆] 的資料行是例外狀況，此資料行表示的是最近一次取樣間隔所得的值。

> [!NOTE]
> 只有在負載測試執行時，名為 [最後一筆] 的資料行才可使用。 當負載測試完成後，這些資料行就無法使用了。

大部分資料表都可以藉由選擇想要排序的資料行標題進行排序。 根據預設，有些資料表並不顯示所有可用的資料行。 如果資料行可以使用，您可以將資料行加入至資料表中。 若要新增資料行，請以滑鼠右鍵按一下資料表，然後選擇 [新增/移除資料行]。

> [!NOTE]
> 表格資料還可以複製到其他應用程式 (例如 Excel)，以便進行其他分析。

## <a name="the-load-test-tables"></a>負載測試資料表

下列表格列出可用於分析負載測試回合的資料表。

|資料表名稱|描述|
|-|-|
|Errors|顯示負載測試回合期間發生的錯誤清單。 如需詳細資訊，請參閱本主題中 [的錯誤資料表](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) ，以及 [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)。|
|頁面|顯示負載測試回合期間存取的頁面清單。 本資料表中的部分資料只有在負載測試完成後才可用。 如需詳細資訊，請參閱 [如何：查看網頁回應](../test/how-to-view-web-page-response-time-in-a-load-test.md)。|
|Requests|顯示負載測試期間所發佈個別要求的詳細資料。 這包含所有 HTTP 要求，以及相依要求 (例如影像)。 如需詳細資訊，請參閱本主題中 [的要求表格](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) 。|
|SQL 追蹤|顯示 SQL 追蹤的結果。 此資料表只有在負載測試完成後，且測試期間有使用 SQL 追蹤時才可用。 如需詳細資訊，請參閱本主題中 [的 SQL 追蹤資料表格](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) 。|
|測試|顯示負載測試期間個別測試回合的詳細資料。 如需詳細資訊，請參閱本主題中 [的測試表格](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) 。|
|臨界值|顯示負載測試回合期間發生的臨界值規則違規清單。 如需詳細資訊，請參閱 [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)。|
|交易|顯示負載測試回合期間發生的異動清單。 如需詳細資訊，請參閱本主題中 [的交易表格](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) 。|
|代理程式|只有當您的負載測試使用測試控制器和測試代理程式時，才會顯示。 顯示負載測試回合期間使用的代理程式清單。 代理程式資料表包含代理程式所測試的要求數目，以及在這些要求中，失敗的要求數目。 此外，代理程式資料表也包含負載測試之測試混合中代理程式所測試的測試數目，以及在這些測試中，失敗的測試數目。|
|測試詳細資料|顯示負載測試之測試混合所包含的測試詳細資料。 這些詳細資料包括測試的名稱、測試所在的情節、測試啟動的時間、執行測試所花費的時間長度，以及指出測試成功或失敗的測試結果。 如果測試失敗，[詳細資料] 資料行就會出現一個連結。 您可以選擇此連結，以便前往 [Web 效能測試編輯器]，其中失敗的要求會反白顯示。|

## <a name="collect-percentile-data"></a>收集百分位數資料

有些負載測試資料表可以包含額外的資料行，其中包含百分位數資料與按照網路模擬而分為群組的回應時間。 根據預設並未收集這個資料。 只有將結果儲存至資料庫時才能使用百分位數資料，在本機儲存時則無法使用。 如需詳細資訊，請參閱 [在 load 測試結果存放庫中管理負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)。 此外，若要收集此資料，請在 [負載測試編輯器] 的 [回合設定] 節點下，選取要變更的特定回合設定節點。 在 [屬性] 視窗中的 [計時詳細資料儲存區] 屬性，選取 [僅限統計資料] 或 [所有個別細節]。 如需詳細資訊，請參閱 [如何：查看網頁回應](../test/how-to-view-web-page-response-time-in-a-load-test.md)。

## <a name="the-requests-table"></a>要求資料表

[要求] 資料表會顯示負載測試期間所發佈個別要求的詳細資料。 這包含所有 HTTP 要求，以及相依要求 (例如影像)。 此資料表是按照測試和情節所列出的，因為一個要求可以包含在許多測試和情節中。

下表列出 [要求] 資料表中的資料行：

|資料行|描述|預設為可見|
|-|-|-|
|**要求**|要求的 URL。 例如：*home.html* 或 *orange-arrow.gif*。|是|
|**案例**|情節的名稱。|是|
|**測試**|測試的名稱。|是|
|**總計**|負載測試回合期間發出的此 Web 效能測試要求總數。 這個總數包含成功和失敗的要求，但不包含快取的要求，因為快取的要求並未發給 Web 伺服器。|是|
|**通過**|發出且成功的要求次數。|否|
|**已失敗**|發出且失敗的要求次數。 此資料行中的項目會顯示成超連結。 您可以選擇任何超連結，以便在 [負載測試錯誤] 對話方塊中檢視個別錯誤的清單。 如需詳細資訊，請參閱 [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)。|是|
|**快取**|已快取之要求的總次數。|否|
|**Requests/Sec**|負載測試期間要求之每秒的速率。|否|
|**成功/秒**|負載測試回合期間此要求之每秒的速率 (針對此要求已成功的執行個體)。|否|
|**失敗/秒**|負載測試回合期間此要求之每秒的速率 (針對此要求已失敗的執行個體)。|否|
|**第一個位元組時間**|接收回應之第一個位元組的平均時間，以要求傳送至 Web 伺服器的時間來計算。 單位為秒數。|否|
|**回應時間**|接收要求的完整回應的平均時間，以要求傳送至 Web 伺服器的時間來計算。 單位為秒數。|是|
|**內容長度**|要求之回應的平均內容長度。 單位為位元組。|是|

## <a name="the-tests-table"></a>測試資料表

[測試] 資料表會顯示負載測試期間個別測試的詳細資料。 此資料表按照測試和情節列出測試，因為一個測試可以包含在許多情節中。

下表列出 [測試] 資料表中的資料行。

|資料行|描述|預設為可見|
|-|-|-|
|**測試**|測試的名稱。|是|
|**案例**|情節的名稱。|是|
|**總計**|情節中測試執行的總次數。 這包含測試成功和失敗的次數。|是|
|**通過**|情節中執行且成功的測試次數。|是|
|**已失敗**|情節中執行但失敗的測試次數。 此資料行中的項目會顯示成超連結。 您可以選擇任何超連結，以便在 [負載測試錯誤] 對話方塊中檢視個別錯誤的清單。 如需詳細資訊，請參閱 [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)。|是|
|**Tests/Sec**|負載測試期間之測試每秒的速率。|是|
|**成功/秒**|負載測試回合期間此測試每秒的速率 (針對此測試已成功的執行個體)。|否|
|**失敗/秒**|負載測試回合期間此測試每秒的速率 (針對此測試已失敗的執行個體)。|否|
|**測試時間**|負載測試回合期間執行測試的平均時間。 單位為秒數。|是|
|**90% 測試時間**|測試時間的第 90 個百分位數。|否|
|**95% 測試時間**|測試時間的第 95 個百分位數。|是|
|**Requests/Test**|在 Web 效能測試中，測試中的要求平均數目。|否|

## <a name="the-transactions-table"></a>異動資料表

[異動] 資料表顯示負載測試回合期間發生的異動清單。 異動是指 Web 效能測試中定義的異動，或是單元測試中定義的計時器。 異動不是指資料庫交易。

下表列出 [異動] 資料表中的資料行。

> [!NOTE]
> 若要檢視所有資料行，您必須啟用與使用中之回合設定相關聯的 [計時詳細資料儲存區] 屬性。 如需詳細資訊，請參閱 [如何：指定計時詳細資料儲存區屬性](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)。

|資料行|描述|可見 (不含計時詳細資料)|
|-|-|-|
|**交易**|交易的名稱。|是|
|**案例**|情節的名稱。|是|
|**測試**|測試的名稱。|是|
|**總計**|負載測試期間發出的異動總數。|是|
|**異動時間**|負載測試回合期間執行異動的時間。 Web 效能測試會將考慮時間一併納入計算。 單位為秒數。|否|
|**回應時間**|負載測試回合中 Web 效能測試異動的回應時間。 回應時間與異動時間不同；回應時間不包括異動期間使用的任何考慮時間。 單位為秒數。|否|
|**平均交易時間**|平均異動時間。 這個時間包括考慮時間。 例如，如果您有三個要求，而且每個要求都具有考慮時間，這個時間就會包括這些考慮時間以及執行要求的實際時間。|否|
|**平均回應時間**|負載測試回合中 Web 效能測試異動的平均回應時間。 回應時間與異動時間不同；回應時間不包括異動期間使用的任何考慮時間。 單位為秒數。|否|
|**最小回應時間**|這不包括考慮時間。|否|
|**最大回應時間**|這不包括考慮時間。|否|
|**中間值回應時間**|這不包括考慮時間。|否|
|**90% 回應時間**|異動時間的第 90 個百分位數。 這不包括考慮時間。 **注意：** 與使用 [90% 異動時間] 值的 Visual Studio Team System 2008 Test Load Agent 有所不同。|否|
|**95% 回應時間**|異動時間的第 95 個百分位數。 這不包括考慮時間。 **注意：** 與使用 [95% 異動時間] 值的 Visual Studio Team System 2008 Test Load Agent 有所不同。|否|
|**99% 回應時間**|異動時間的第 99 個百分位數。 這不包括考慮時間。|否|
|**標準差回應時間**|這不包括考慮時間。|否|

## <a name="the-errors-table"></a>錯誤資料表

當您執行負載測試時，可以分析其中發生的錯誤。 分析錯誤和調整測試，是負載測試程序中很重要的一部分。 如果發生錯誤，負載測試狀態列會出現 [錯誤] 超連結，並指出錯誤發生的數量。 若要顯示錯誤資料表，請選擇超連結。

錯誤資料表會根據錯誤的類型與子類型，將負載測試期間發生的錯誤分組。 資料表中的 **總** 行數表示所發生錯誤的總數。

錯誤資料表包含下列資料行：

|資料行|描述|預設為可見|
|-|-|-|
|類型|錯誤的類型。 例如，HttpError。|是|
|子類型|錯誤的子類型。 例如，LoadTestException。|是|
|計數|負載測試期間發生此類型錯誤的數量。 此資料行中的項目會顯示成超連結。 您可以選擇任何超連結，檢視個別錯誤的清單。|是|
|最後一個訊息|描述錯誤的訊息。 例如，404 - NotFound。|是|

如需詳細資訊，請參閱 [使用負載測試資料表](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

### <a name="drill-down-to-the-error-list"></a>向下切入錯誤清單

錯誤資料表會根據錯誤的類型與子類型，將錯誤分組。 若要檢視個別錯誤的資料表，請顯示 [負載測試錯誤] 對話方塊。 若要顯示這個對話方塊，請選擇錯誤資料表的 [計數] 資料行中的超連結。 您也可以在已填入的錯誤資料表中，以滑鼠右鍵按一下資料列，然後選擇 [錯誤] 顯示對話方塊。

> [!NOTE]
> 只有所有錯誤類型及子類型最前面 1000 個例項才會予以收集。 當您顯示 [負載測試錯誤] 對話方塊時，最多只會看到該錯誤最前面 1,000 個例項。

[負載測試錯誤] 資料表包含下列資料行：

|資料行|描述|
|-|-|
|**Time**|負載測試期間發生錯誤的時間。|
|**代理程式**|發生錯誤之代理程式電腦的名稱。 這在您使用測試控制器和測試代理程式執行負載測試時相當重要。 如需詳細資訊，請參閱[安裝和設定測試代理程式](../test/lab-management/install-configure-test-agents.md)。|
|**測試**|發生錯誤之 Web 效能測試的名稱。|
|**案例**|發生錯誤之情節的名稱。|
|**要求**|發生錯誤之要求的 URL。|
|**型別**|錯誤的類型。 例如，HttpError。|
|**子類型**|錯誤的子類型。 例如，LoadTestException。|
|**Text**|錯誤訊息的文字。 例如，404 - NotFound。|
|**堆疊**|本資料行中的項目一定是空的，或是超連結格式的 **Stack** 一字。 您可以選擇超連結，檢視錯誤的堆疊追蹤。|
|**詳細資料**|本資料行中的項目一定是空的，或是超連結格式的 **TestLog** 一字。 此連結可幫助您找出負載測試中的錯誤。 例如，選擇 web 效能測試要求錯誤上的 [ **TestLog** ] 連結，就會在 [Web 效能] 測試結果檢視器中開啟 web 效能測試的結果，並醒目提示要求錯誤。|

> [!NOTE]
> 選擇資料行標頭即可排序資料表。

## <a name="the-sql-trace-data-table"></a>SQL 追蹤資料表

在負載測試回合期間，您可以收集 SQL 追蹤資料以便稍後進行分析。 收集追蹤資料可讓您識別要測試的 SQL Server 資料庫中，執行最慢的查詢和預存程序 (Stored Procedure)。

如果啟用了 SQL 追蹤，在進行包含追蹤資料的負載測試回合時，就會建立一個檔案。 在測試回合結束時，這項資料會自動儲存至「負載測試結果存放區」，而且會將上述追蹤檔刪除。 負載測試完成後，您可以在 [SQL 追蹤] 資料表中分析追蹤資料。

### <a name="to-view-sql-trace-data"></a>檢視 SQL 追蹤資料

1. 在 [負載測試分析器] 中，選擇工具列上的 [資料表]，確定資料表格線已顯示。

2. 在 [資料表] 下拉式清單方塊中，選取 [SQL 追蹤]。

3. 在回合期間所收集的追蹤資料便會顯示在方格中。 該資料表會依照持續期間列出執行最慢的 SQL 作業，最慢的排在最上面。 通常，[持續期間] 資料行是第一個要檢視的資料行。 資料是以毫秒為單位顯示。

   顯示的資料行如下所示：

    - **Event Class**

    - **有效期間**

    - **CPU**

    - **Reads**

    - **Writes**

    - **TextData**

    - **StartTime**

    - **EndTime**

   如果您想要追蹤這些資料行所識別之資料以外的 SQL 事件，可以使用 SQL Profiler 工具 (與 Visual Studio 分開的獨立工具) 設定自訂 SQL 追蹤。

## <a name="tile-load-test-tables"></a>並排顯示負載測試資料表

在您檢視負載測試回合的結果時，可以採用詳細資料表的形式來檢視資料。 若要切換到資料表視圖，請選擇 [**負載測試**] 工具列上的 [**資料表]** 。 可用的資料表包括 [錯誤]、[頁面]、[要求]、[SQL 追蹤]、[測試]、[臨界值] 和 [異動]。 如需詳細資訊，請參閱 [使用負載測試資料表](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

在資料表檢視中，您一次最多可以檢視四份資料表 (在資料表不重疊的情況下)。

### <a name="to-tile-tables"></a>若要並排顯示資料表

1. 在 [ **負載測試分析器** ] 工具列上，選擇 [ **資料表]**。

     [資料表] 檢視隨即開啟。 預設配置為兩個水平面板。

2. 在 [負載測試分析器] 工具列上，選擇 [配置] 按鈕，然後選擇下列其中一個選項：

    - **一個面板**

    - **兩個水平面板**

    - **三個水平面板**

    - **四個水平面板**

3. 若要在不同的資料表之間切換，請使用每個面板中資料表方格上方的下拉式清單。

    > [!NOTE]
    > 您不能在多個面板中顯示同一份資料表。 如果將某個面板中顯示的資料表變更為另一個面板已經顯示的資料表，這兩個資料表的面板就會交換。

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)
- [在圖表檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)
- [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [負載測試結果摘要概觀](../test/load-test-results-summary-overview.md)
