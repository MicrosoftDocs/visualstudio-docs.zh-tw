---
title: HOW TO：從存放庫中刪除負載測試結果
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e351ccaa6dddcf4773169a1e0a3f8e074002f2d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936118"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>HOW TO：從存放庫中刪除負載測試結果

當您執行負載測試時，執行期間所收集到的資訊，都會儲存在負載測試結果儲存機制中。 負載測試結果儲存機制含有效能計數器資料，以及錄製之錯誤的相關資訊。 如需詳細資訊，請參閱[管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)。

您可以使用 [開啟和管理負載測試結果] 對話方塊，在負載測試編輯器中管理負載測試結果。 您可以開啟、匯入、匯出及移除負載測試結果。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>若要從儲存機制刪除結果

1.  從 Web 效能和負載測試專案中，開啟負載測試。

2.  在內嵌工具列上，選擇 [開啟和管理結果]。

     [開啟和管理負載測試結果] 對話方塊隨即出現。

3.  在 [輸入控制器名稱以尋找負載測試結果] 中，選取控制器。 選取 [\<本機 - 無控制器>]，存取儲存在本機的結果。

4.  在 [顯示下列負載測試的結果] 中，選取您要檢視其結果的負載測試。 選取 [\<顯示所有測試的結果>]，即可查看所有測試的所有結果。

     如果有可用的負載測試結果，它們會出現在 [負載測試結果] 清單中。 資料行包括 [時間]、[持續期間]、[使用者]、[結果]、[測試] 和 [描述]。 [測試] 包含測試的名稱，而 [描述] 則包含執行測試之前所新增的選擇性描述。 [描述] 資料行顯示的是在此測試結果之 [分析註解] 中輸入的簡短描述。

5.  在 [負載測試結果] 清單中，選擇一個結果。 您可以使用 **Shift** 鍵和 (或) **Ctrl** 鍵來選取多個結果。

6.  選擇 [移除]。

     結果隨即從儲存機制中移除。

    > [!NOTE]
    > 移除結果之後，[開啟和管理負載測試結果] 對話方塊仍會繼續保持開啟。

## <a name="see-also"></a>另請參閱

- [如何：從存放庫匯出負載測試結果](../test/how-to-export-load-test-results-from-a-repository.md)
- [管理負載測試結果儲存機制中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [如何：將負載測試結果匯入存放庫](../test/how-to-import-load-test-results-into-a-repository.md)