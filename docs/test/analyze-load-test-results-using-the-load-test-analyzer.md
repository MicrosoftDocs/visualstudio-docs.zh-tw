---
title: 分析負載測試結果
description: 瞭解如何使用負載測試分析器找出瓶頸、找出錯誤，以及測量應用程式中的改善。
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f33898aa1c3c08179f1438a7c6e6e11a75587bc
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442478"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>使用負載測試分析器分析負載測試結果

當您使用 [負載測試分析器] 時，可以找出應用程式的瓶頸、辨識應用程式的錯誤，以及測量應用程式的改善程度。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

您可以透過下列方式來分析負載測試結果：

- 在負載測試執行時予以監視。

- 在負載測試完成後予以分析。

- 檢視上一次負載測試的結果。

您也可以建立報告，這些報告會比較兩個以上的報告以進行趨勢分析，並與專案關係人共用。 請參閱[針對測試比較或趨勢分析報告負載測試結果](../test/compare-load-test-results.md)。

不論您是從 Visual Studio Enterprise 或命令列執行負載測試，也不論您是在單機電腦或遠端機器上執行負載測試，都可以完成上述工作。

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>分析執行中與已完成之負載測試之間的差異

當您執行負載測試時，[負載測試分析器] 會顯示在另一個索引標籤中，並顯示負載測試的名稱以及測試開始的時間 (例如 **LoadTest1 [12:40 PM]**)。 當負載測試執行時，會有較小的一組效能計數器資料維持在記憶體中。 您可以在負載測試執行時監視這組資料。 負載測試完成之後，您可以從資料庫分析整組資料。 負載測試執行時顯示的資料，與負載測試完成後可以看到的資料之間有一些差異。 例如，90% 和 95% 的回應時間資料都必須等到負載測試完成後才會進行計算。 而且可以用來分析資料之工具的功能也有一些差異。

在您執行負載測試時，可使用兩個檢視：[圖形] 測試和 [資料表] 檢視。 [圖形] 檢視可讓您繪製所收集的效能計數器。 [資料表] 檢閱提供每個收集的測試、頁面、異動和要求的資訊。 您也可以取得列出錯誤的資料表。

根據預設，當負載測試完成時，會顯示 [摘要] 檢視。 您可以使用工具列在 [摘要]、[圖形]、[資料表] 和 [詳細資料] 檢視之間切換。 [負載測試分析器] 可以使用一般的 Visual Studio 視窗管理技術，設為停駐或浮動視窗。 當您分析完成的負載測試回合時，可以同時開啟多個 [負載測試分析器]，以比較不同的負載測試回合。

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-|
|**存取負載測試的結果：** 當您從 [負載測試編輯器] 執行負載測試時，負載測試結果會自動開啟，而且執行中的負載測試會顯示在 [負載測試分析器] 中。|-   [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)|
|**在負載測試中新增分析注意事項：** 您可以在進行分析時將註解新增至負載測試。 註解會隨著負載測試結果永久儲存。 您輸入的描述也會顯示在 [ **描述** ] 資料行中，此資料行與 [ **開啟和管理測試結果** ] 對話方塊中的負載測試相關聯的負載測試編輯器。<br /><br /> 如需詳細資訊，請參閱 [如何：存取負載測試結果以進行分析](../test/how-to-access-load-test-results-for-analysis.md)。<br /><br /> 此外，當您建立負載測試結果的 Excel 報表時，就會顯示註解。<br /><br /> 如需詳細資訊，請參閱 [針對測試比較或趨勢分析報告負載測試結果](../test/compare-load-test-results.md)。||
|**分析負載測試的結果：** 您必須先存取負載測試回合資料，之後才能分析產生的資料。 您可以檢視 [負載測試摘要]，快速了解測試的結果。 負載測試摘要會以精簡易讀的格式顯示主要的結果。<br /><br /> 您可以列印負載測試摘要， 以方便您和專案關係人一起討論測試的結果。<br /><br /> 您可以使用負載測試結果中的圖形和資料表，分析負載測試結果的詳細資料。 其中包括 [錯誤]、[頁面]、[要求]、[SQL 追蹤]、[測試]、[臨界值] 和 [異動]。|-   [負載測試結果摘要總覽](../test/load-test-results-summary-overview.md)<br />-   [如何：檢視網頁回應](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [在圖形視圖中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [在資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**分析負載測試結果中的虛擬使用者活動，以找出效能問題：** 您可以使用「虛擬使用者活動圖」，以視覺化虛擬使用者在負載測試期間的行為。 這樣可幫助您找出 CPU 使用率激增或者要求數/秒降低的狀況，並判斷發生這些狀況時正在執行的測試或頁面。|-   [在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
