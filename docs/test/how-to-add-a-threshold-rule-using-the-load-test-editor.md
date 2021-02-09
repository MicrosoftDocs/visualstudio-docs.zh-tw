---
title: 新增用於負載測試的臨界值規則
description: 瞭解負載測試中的臨界值規則，這些規則會比較效能計數器值與常數值或另一個效能計數器值。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: aa8e9af0c4ca25b29e0194e5515250ceb4cd6254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908650"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>如何：使用負載測試編輯器新增臨界值規則

負載測試中的臨界值規則會將效能計數器值與常數值或其他效能計數器值做比較。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>加入臨界值規則

1. 開啟負載測試。

2. 在 [負載測試編輯器] 中，展開 [計數器集合] 節點。

3. 在其中一個計數器集合中，展開其中一個 [計數器分類]。 例如，您可以選取 [LoadTest:Scenario]。 展開這個節點。

4. 以滑鼠右鍵按一下其中一個計數器，例如 [LoadTest:Scenario] 下的 [User Load]。 選取 [新增臨界值規則]。

     [新增臨界值規則] 對話方塊隨即出現。

5. 您可以選擇兩種規則類型：**比較常數** 和 **比較計數器**。 請選取適當的類型並設定其值。

    > [!NOTE]
    > 將 [超出時提醒] 屬性設定為 [True]，表示超出臨界值會是一個問題，或設為 [False]，表示未達臨界值會是一個問題。

## <a name="see-also"></a>另請參閱

- [分析臨界值規則違規](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [在負載測試中指定電腦的計數器集合和臨界值規則](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [分析負載測試結果](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
