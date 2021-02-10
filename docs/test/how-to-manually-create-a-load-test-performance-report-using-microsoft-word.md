---
title: 使用 MS Word 建立負載測試效能報表
description: 瞭解如何藉由從 [載入測試結果摘要] 和 [圖形] 視圖複製和貼上資料，手動建立 Microsoft Word 負載測試報告。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a7b5246e75b226c04f7dfa2e0e649bcdb85afe8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971878"
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>如何：使用 Microsoft Word 手動建立負載測試效能報告

您可以從 [負載測試結果] 摘要檢視和圖表檢視複製並貼上資料，藉以手動建立 Microsoft Word 負載測試報告。 當您複製呈現在摘要檢視和圖形檢視中的資料時，這項資料會套用 HTML 格式。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> 您可以將資料表檢視中的純文字和詳細資料檢視中的螢幕擷取畫面複製到 Microsoft Word，但是這些項目不會套用 HTML 格式，而且需要進行其他格式設定和編輯。

> [!TIP]
> 您也可以自動產生組織化的 Microsoft Excel 報告。 如需詳細資訊，請參閱[如何：使用 Microsoft Excel 建立負載測試效能報告](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)。

## <a name="copy-summary-view-data"></a>複製摘要檢視資料

1. 在 [負載測試結果] 中，如果目前沒有顯示摘要檢視，請按一下工具列中的 [摘要]。

2. 在摘要檢視中，按一下滑鼠右鍵，然後選取 [全選]。

3. 在摘要檢視中，按一下滑鼠右鍵，然後選取 [複製]。 這樣就會將摘要檢視資料當做 HTML 格式呈現至 [剪貼簿]。

4. 在 Microsoft Word 中，將摘要檢視資料貼入所需的位置。

5. 您現在可以修改、格式化並刪除所複製內容的各個層面，以便符合您的報告需求。

## <a name="copy-graph-view-data"></a>複製圖表檢視資料

1. 在 [負載測試結果] 中，如果目前沒有顯示圖表檢視，請選擇工具列中的 [圖表]。

2. (選擇性) 放大您想要複製到 Microsoft Word 文件的特定圖表，如下圖所示。 如需詳細資訊，請參閱 [如何：放大圖形的某個區域](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)。

     ![圖形檢視縮放控制](../test/media/ltest_zoomcontrol.png)

3. 在您想要複製到 Microsoft Word 文件的圖表上，按一下滑鼠右鍵，然後選取 [複製]。

4. 在 Microsoft Word 中，將圖表和相關聯的資料表資料貼入所需的位置。

    > [!WARNING]
    > 您無法從遠端桌面複製圖形並將它貼入另一部電腦，因為系統只會複製與圖形相關聯的資料表資訊，而非圖形影像。 圖形影像會儲存在從中複製圖形之電腦的暫存目錄中，而且第二部電腦無法取值該目錄。

## <a name="see-also"></a>另請參閱

- [針對測試比較或趨勢分析報告負載測試結果](../test/compare-load-test-results.md)
- [如何：使用 Microsoft Excel 建立負載測試效能報告](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)
