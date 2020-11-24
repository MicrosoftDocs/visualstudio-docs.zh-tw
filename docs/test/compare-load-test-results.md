---
title: 分析負載測試結果
description: 瞭解如何根據兩個以上的測試結果產生 Excel 負載測試報告，包括執行比較報表和趨勢報表。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 66a388b5b6d74834c58eebad04147d5067655a28
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441590"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>針對測試比較或趨勢分析報告負載測試結果

您可以根據兩個或多個測試結果，產生 Microsoft Excel 負載測試報告。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

共有兩種負載測試報告可供使用：

- 執行比較&mdash;這個報告其實是兩個報告，可使用資料表和橫條圖並排顯示比較資料。

- 趨勢&mdash;您可以在兩個或多個報告上產生趨勢分析。 結果會以折線圖顯示。

上述兩種報告都能用來與專案關係人共用效能資料，傳達出整體效能和系統的健康狀況是變好還是變差。

報告定義儲存在負載測試資料庫中。 儲存報告時，報告的定義是儲存在資料庫中，稍後可以重複使用。

此外，也能和專案關係人共用試算表檔案，因此專案關係人不必連接至資料庫就能查看報告。

> [!NOTE]
> 如果您將註解新增至負載測試，這些註解就會顯示在 Excel 報表中。

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-|
|**建立效能與壓力報告：** 您可以使用 Microsoft Excel，建立負載測試與 Web 效能測試的報告。|- [如何：使用 Microsoft Excel 建立負載測試效能報表](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**使用 Microsoft Word 手動建立效能與壓力報告：** 您可以透過將摘要、資料表和圖形資料複製並貼入 Microsoft Word 文件，手動建立負載和 Web 效能測試的報告。|- [如何：使用 Microsoft Word 手動建立負載測試效能報表](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
