---
title: 分析負載測試虛擬使用者活動
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591230"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>在負載測試分析器的詳細資料檢視中分析負載測試虛擬使用者活動

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**虛擬使用者活動圖**

![虛擬使用者活動圖](../test/media/virtual_actchart.png)

[詳細資料]**** 檢視中顯示的 [虛擬使用者活動圖]**** 可用來以視覺方式分析個別虛擬使用者在負載測試期間的行為。 [虛擬使用者活動圖]**** 可讓您查看使用者活動模式、負載模式、將失敗或緩慢的測試相互關聯，以及查看其他虛擬使用者活動的要求。 [虛擬使用者活動圖]**** 也可幫助您決定 CPU 使用量突然增加的問題、每秒要求中降低的情形，以及發生這些狀況時正在執行的測試或頁面。

> [!NOTE]
> 在運行要使用**虛擬使用者活動詳細資訊圖表**的負載測試之前，必須使用載入效能測試編輯器驗證**計時詳細資訊存儲**屬性是否設置為 **"所有個人詳細資訊"** 選項。

**詳細資訊圖例面板**

![詳細資料圖例面板](../test/media/ltest_detailslegend.png)

詳細資料圖例面板會顯示在 [虛擬使用者活動圖]**** 中。 詳細資料圖例窗格可讓您根據不同準則，篩選出測試、頁面和異動。 例如，您可以從檢視中移除特定測試、移除所有順利完成的測試，或移除因特定因素而失敗的測試。 您也可以移除不具有記錄的所有測試。

您可以反白顯示失敗的測試，進而以紅色顯示所有失敗的測試。 您也可以反白顯示具有測試記錄的測試。 會以綠色顯示具有記錄的測試。

**篩選結果面板**

![篩選結果面板](../test/media/ltest_filterresults.png)

篩選結果面板會顯示在 [虛擬使用者活動圖]**** 中。 篩選結果面板可篩選下列項目：

- **只顯示有記錄檔的結果**：僅顯示具有關聯測試記錄檔的測試結果。

- **顯示成功的結果**：顯示成功的結果。

- **顯示有錯誤的結果** 顯示具有錯誤的結果，這些錯誤可協助偵錯。

## <a name="tasks"></a>工作

|工作|相關主題|
|-|-|
|**運行負載測試：** 創建負載測試並將其配置為啟用虛擬使用者活動資料收集後，必須運行測試，直到完成測試才能查看**虛擬使用者活動圖表**。||
|**查看包含虛擬使用者活動資料的負載測試結果：** 創建、配置負載測試並完成運行後，可以使用**虛擬使用者活動圖表查看虛擬使用者活動**資料。|-   [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [如何：分析虛擬使用者在負載測試期間執行的操作](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**隔離負載測試中的性能問題：** 您可以使用**虛擬使用者活動圖表**來説明隔離負載測試中的性能問題。|-   [演練：使用虛擬使用者活動圖表隔離問題](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [分析表視圖中的負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
