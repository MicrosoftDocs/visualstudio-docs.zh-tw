---
title: 如何：評估 XPath 運算式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670873"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>HOW TO：評估 XPath 運算式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [ **快速** 監看式] 對話方塊來評估 XPath 運算式。 根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。 目前的 XSLT 內容（也就是 `self::node()` [ **區域變數** ] 視窗中的節點）會提供 XPath 運算式的評估內容。

 下列清單說明當評估 XPath 運算式時，支援哪些函式：

- 支援內建 XPath 函式。

- 不支援內建 XSLT 函式。

- 不支援使用者定義函式。

> [!NOTE]
> 下列程式會使用 [逐步解說： DEBUG XSLT 樣式表單](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) 主題中的 belowAvg xsl 和 books.xml 檔案。

### <a name="to-evaluate-an-xpath-expression"></a>評估 XPath 運算式

1. 在 `xsl:if` 開始標記處插入中斷點。

2. 在 [XML 編輯器] 工具列上，按一下 [ **DEBUG XSL** ] 按鈕。

     偵錯工具會啟動，並在 `xsl:if` 標記處中斷。

3. 以滑鼠右鍵按一下並選取 [ **快速**監看式]。

     [ **快速** 監看式] 對話方塊隨即顯示。

4. 在 [監看式 `./price/text()` ] 對話方塊的 [**運算式**] 欄位中輸入，然後按一下 **[重新****評估**]。

     [目前的書籍] 節點的價格會出現在 [ **值** ] 方塊中。

5. 將 XPath 運算式變更為 `./price/text() < $bookAverage` ，然後按一下 [重新 **評估**]。

     [ **值** ] 方塊會顯示 XPath 運算式評估為 `true` 。

## <a name="see-also"></a>另請參閱
 [偵錯 XSLT](../xml-tools/debugging-xslt.md)
