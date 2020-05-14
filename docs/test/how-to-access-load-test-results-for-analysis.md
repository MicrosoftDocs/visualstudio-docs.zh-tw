---
title: 分析負載測試結果
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6a5da728e24d5d7fdbeccd1e28aa2742e04bf48
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596459"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>如何：存取負載測試結果以進行分析

當您從 [負載測試編輯器] 執行負載測試時，負載測試結果會自動開啟，而且執行中的負載測試會顯示在 [負載測試分析器]**** 中。 當您從命令列執行負載測試時，必須手動存取負載測試結果。

已完成之負載測試的負載測試結果包含效能計數器樣本，以及定期從受測電腦收集而來的錯誤資訊。 您可以在負載測試回合進行期間收集大量效能計數器樣本。 收集的效能資料量會視測試回合的長度、取樣間隔、受測電腦數量、收集的計數器數量、設定的資料收集器，以及記錄層級而定。 若為大型負載測試，所收集的效能資料數量可能很輕易就達到數 GB。 有關詳細資訊，請參閱[測試控制器和測試代理](configure-test-agents-and-controllers-for-load-tests.md)。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>存取負載測試結果

1. 從 Web 效能和負載測試專案中，開啟負載測試。

2. 在 [負載測試編輯器] 的工具列中，選擇 [開啟和管理結果]**** 按鈕。

     [開啟和管理結果]**** 對話方塊隨即出現。

3. 在 [輸入控制器名稱以尋找負載測試結果]**** 中，選取控制器。 選擇**\<本地> - 沒有控制器**訪問存儲在本地的結果。

4. 在 [顯示下列負載測試的結果]**** 中，選取您要檢視其結果的負載測試。 選擇**\<"顯示所有測試的結果>** 以查看所有測試的所有結果。

     如果有可用的負載測試結果，它們會出現在 [負載測試結果]**** 清單中。 資料行包括 [時間]****、[持續期間]****、[使用者]****、[結果]****、[測試]**** 和 [描述]****。 [測試]**** 包含測試的名稱，而 [描述]**** 則包含執行測試之前所新增的選擇性描述。

    > [!NOTE]
    > 結果隨即出現；最新的結果顯示在清單最上方。

5. 在 [負載測試結果]**** 清單中，選取您要分析的負載測試結果，然後選擇 [開啟]****。

6. [負載測試分析器]**** 隨即顯示。 選取的負載測試結果會顯示在 [摘要] 檢視中。 如需詳細資訊，請參閱[負載測試結果摘要概觀](../test/load-test-results-summary-overview.md)。

     您可以在 [開啟和管理結果]**** 對話方塊中管理負載測試結果的其他方面，包括匯入、匯出和移除負載測試結果。 如需詳細資訊，請參閱[管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)。

## <a name="see-also"></a>另請參閱

- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
