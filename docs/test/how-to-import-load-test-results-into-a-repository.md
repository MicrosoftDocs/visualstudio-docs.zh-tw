---
title: 如何：將負載測試結果匯入至儲存機制
description: 瞭解如何使用 [開啟和管理載入測試結果] 對話方塊，將資訊載入載入測試結果存放庫。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: df32fa09b95a9adfbc245ff5c3ec3ab9fbabd1d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961452"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>如何：將負載測試結果匯入至存放庫

當您執行負載測試時，執行期間所收集到的資訊，都會儲存在負載測試結果儲存機制中。 負載測試結果儲存機制含有效能計數器資料，以及錄製之錯誤的相關資訊。 如需詳細資訊，請參閱 [在 load 測試結果存放庫中管理負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)。

您可以使用 [開啟和管理負載測試結果] 對話方塊，在負載測試編輯器中管理負載測試結果。 您可以開啟、匯入、匯出及移除負載測試結果。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>若要將結果匯入至儲存機制

1. 從 Web 效能和負載測試專案中，開啟負載測試。

2. 在內嵌工具列上，選擇 [開啟和管理結果]。

     [開啟和管理負載測試結果] 對話方塊隨即出現。

3. 在 [輸入控制器名稱以尋找負載測試結果] 中，選取控制器。 選取 **\<local>** 即可存取儲存在本機的結果。

     如果有可用的負載測試結果，它們會出現在 [負載測試結果] 清單中。 資料行包括 [時間]、[持續期間]、[使用者]、[結果]、[測試] 和 [描述]。 [測試] 包含測試的名稱，而 [描述] 則包含執行測試之前所新增的選擇性描述。

4. 選擇 [匯入]。

     [匯入負載測試結果] 對話方塊隨即出現。

5. 在 [檔名] 方塊中輸入封存測試結果檔案的名稱，然後選擇 [開啟]。

     \- 或 -

     瀏覽至該檔案，然後選擇 [開啟]。

    > [!NOTE]
    > 您在這個步驟指定的封存測試結果檔案必須已經透過執行 [匯出] 作業建立完成。

     結果隨即匯入，並出現在 [負載測試結果] 清單中。

## <a name="see-also"></a>另請參閱

- [管理負載測試結果存放庫中的負載測試結果](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [如何：從存放庫匯出負載測試結果](../test/how-to-export-load-test-results-from-a-repository.md)
