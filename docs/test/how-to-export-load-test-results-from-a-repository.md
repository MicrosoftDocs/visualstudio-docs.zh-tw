---
title: 匯出負載測試結果
description: 瞭解如何使用 [開啟和管理載入測試結果] 對話方塊，從 Load 測試結果儲存機制匯出資訊。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 960605dd35a30af1b2c8933d24cfa80ebb97f6c1
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439907"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>如何：從存放庫匯出負載測試結果

當您執行負載測試時，執行期間所收集到的資訊，都會儲存在負載測試結果儲存機制中。 負載測試結果儲存機制含有效能計數器資料，以及錄製之錯誤的相關資訊。 如需詳細資訊，請參閱 [在 load 測試結果存放庫中管理負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)。

您可以使用 [開啟和管理負載測試結果] 對話方塊，在負載測試編輯器中管理負載測試結果。 您可以開啟、匯入、匯出及移除負載測試結果。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>若要從儲存機制匯出結果

1. 從 Web 效能和負載測試專案中，開啟負載測試。

2. 在內嵌工具列上，選擇 [開啟和管理結果]。

     [開啟和管理負載測試結果] 對話方塊隨即出現。

3. 在 [輸入控制器名稱以尋找負載測試結果] 中，選取控制器。 選取 **\<Local - No controller>** 即可存取儲存在本機的結果。

4. 在 [顯示下列負載測試的結果] 中，選取您要檢視其結果的負載測試。 選取 **\<Show results for all tests>** 即可查看所有測試的所有結果。

     如果有可用的負載測試結果，它們會出現在 [負載測試結果] 清單中。 資料行包括 [時間]、[持續期間]、[使用者]、[結果]、[測試] 和 [描述]。 [測試] 包含測試的名稱，而 [描述] 則包含執行測試之前所新增的選擇性描述。 [描述] 資料行顯示的是在此測試結果之 [分析註解] 中輸入的簡短描述。

5. 在 [負載測試結果] 清單中，選擇一個結果。 您可以使用 **Shift** 鍵和 (或) **Ctrl** 鍵來選取多個結果，再將它們匯出成單一檔案。

6. 選擇 [匯出]。

     [匯出負載測試結果] 對話方塊隨即出現。

7. 在 [檔案名稱] 方塊中鍵入名稱，然後選擇 [儲存]。

     結果隨即匯出為封存檔。

    > [!NOTE]
    > 在結果出現之後，[開啟和管理負載測試結果] 對話方塊仍會繼續保持開啟。

## <a name="see-also"></a>另請參閱

- [管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [如何：從存放庫中刪除負載測試結果](../test/how-to-delete-load-test-results-from-a-repository.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [如何：將負載測試結果匯入至存放庫](../test/how-to-import-load-test-results-into-a-repository.md)
