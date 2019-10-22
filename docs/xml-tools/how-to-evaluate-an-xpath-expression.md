---
title: 在進行偵錯工具時評估 XPath 運算式
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 523c89af70c762f0cd0e31519c8c862c440c79eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654279"
---
# <a name="evaluate-xpath-expressions"></a>評估 XPath 運算式

您可以在偵錯工具期間使用 [**快速**監看式] 視窗來評估 XPath 運算式。 根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。 目前的 XSLT 內容（也就是 [**區域變數**] 視窗中的 [`self::node()`] 節點）會提供 XPath 運算式的評估內容。

評估 XPath 運算式時：

- 支援內建 XPath 函式。

- 不支援內建 XSLT 函數和使用者定義函數。

> [!NOTE]
> 只有 Visual Studio 的 Enterprise edition 才可使用 XSLT 調試。

## <a name="evaluate-an-xpath-expression"></a>評估 XPath 運算式

下列程式會使用[逐步解說： Debug a XSLT 樣式表單](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files)頁面中的*below-average. xsl*和*books.xml*檔案。

1. 在 `xsl:if` 開始標記處插入中斷點。

2. 若要開始進行調試，請選擇 [ **XML** ]  >  在功能表列上**啟動 XSLT 調試**（或按**Alt** +**F5**）。

   偵錯工具會啟動，並在 `xsl:if` 標記處中斷。

3. 以滑鼠右鍵按一下並選取 [**快速**監看式]。

   [**快速**監看式] 視窗隨即開啟。

4. 在 [**快速**監看式] 對話方塊的 [**運算式**] 欄位中輸入 `./price/text()`，然後選擇 [重新**評估**]。

   [目前的書籍] 節點的價格會顯示在 [**值**] 方塊中。

   ![在 [快速監看式] 視窗中評估 XPath 運算式](media/quickwatch-price.png)

5. 將 XPath 運算式變更為 `./price/text() < $bookAverage`，然後按一下 [重新**評估**]。

   [**值**] 方塊會顯示 XPath 運算式會評估為 `true`。

## <a name="see-also"></a>請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)