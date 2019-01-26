---
title: HOW TO：評估 XPath 運算式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ab895bb10c9f1b70ba103aebeb0ad83cdb84418
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000974"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>HOW TO：評估 XPath 運算式

您可以評估 XPath 運算式與**快速監看式** 對話方塊。 根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。 目前的 XSLT 內容 — 也就是`self::node()`中的節點**區域變數**視窗，提供 XPath 運算式的評估內容。

 下列清單說明當評估 XPath 運算式時，支援哪些函式：

-   支援內建 XPath 函式。

-   不支援內建 XSLT 函式。

-   不支援使用者定義函式。

> [!NOTE]
> 使用下列程序*belowAvg.xsl*並*books.xml*檔案從[逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)主題。

## <a name="to-evaluate-an-xpath-expression"></a>評估 XPath 運算式

1.  在 `xsl:if` 開始標記處插入中斷點。

2.  按一下 **偵錯 XSL** XML 編輯器工具列上的按鈕。

     偵錯工具會啟動，並在 `xsl:if` 標記處中斷。

3.  以滑鼠右鍵按一下並選取**快速監看式**。

     **快速監看式**對話方塊隨即出現。

4.  請輸入`./price/text()`中**運算式**欄位**快速監看式**對話方塊中，然後按一下**重新評估**。

     目前書籍節點的價格會出現在**值** 方塊中。

5.  將 XPath 運算式變更為`./price/text() < $bookAverage`，按一下 **重新評估**。

     **值** 方塊會顯示 XPath 運算式評估為`true`。

## <a name="see-also"></a>另請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)