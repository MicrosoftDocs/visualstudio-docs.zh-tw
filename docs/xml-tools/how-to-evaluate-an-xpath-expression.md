---
title: HOW TO：評估 XPath 運算式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2956e0c19e7cf50fdde39765bc5b26112986b84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>HOW TO：評估 XPath 運算式

您可以評估 XPath 運算式與**快速監看式** 對話方塊。 根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。 目前的 XSLT 內容 — 也就是`self::node()`中的節點**區域變數**視窗，提供 XPath 運算式的評估內容。

 下列清單說明當評估 XPath 運算式時，支援哪些函式：

-   支援內建 XPath 函式。

-   不支援內建 XSLT 函式。

-   不支援使用者定義函式。

> [!NOTE]
> 下列程序會使用 belowAvg.xsl 及 books.xml 檔[逐步解說： 偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)主題。

## <a name="to-evaluate-an-xpath-expression"></a>評估 XPath 運算式

1.  在 `xsl:if` 開始標記處插入中斷點。

2.  按一下**偵錯 XSL** XML 編輯器工具列上的按鈕。

     偵錯工具會啟動，並在 `xsl:if` 標記處中斷。

3.  以滑鼠右鍵按一下並選取**快速監看式**。

     **快速監看式**對話方塊隨即出現。

4.  輸入`./price/text()`中**運算式**欄位**快速監看式**對話方塊，按一下**重新評估**。

     目前的書籍節點的價格會出現在**值**方塊。

5.  將 XPath 運算式變更為`./price/text() < $bookAverage`按一下**重新評估**。

     **值**方塊會顯示 XPath 運算式評估為`true`。

## <a name="see-also"></a>另請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)