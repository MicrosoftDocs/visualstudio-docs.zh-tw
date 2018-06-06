---
title: 逐步解說：偵錯 XSLT 樣式表
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebc8e8f8700690a2ae74fcc91384fb77b238ea33
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693392"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>逐步解說： 偵錯 XSLT 樣式表

此逐步教學中的步驟示範如何使用 XSLT 偵錯工具。 這些步驟包括檢視變數、設定中斷點及逐步執行程式碼。 樣式表會尋找低於書籍價格平均值的所有書籍。

## <a name="to-prepare-for-this-walkthrough"></a>準備此逐步教學

1.  關閉任何開啟的解決方案。

2.  將兩個範例檔案複製到本機電腦。

## <a name="start-debugging"></a>開始偵錯

### <a name="to-start-debugging"></a>若要啟動偵錯

1.  從**檔案**功能表上，指向**開啟**，然後按一下**檔案**。

2.  找出*belowAvg.xsl*檔案，然後按一下 **開啟**。

     樣式表會在 XML 編輯器中開啟。

3.  按一下瀏覽按鈕 (**...**) 上**輸入**文件屬性 視窗的欄位。

4.  找出*books.xml*檔案，然後按一下 **開啟**。

     這會設定用於 XSLT 轉換的來源文件檔案。

5.  以滑鼠右鍵按一下`xsl:if`開始標記、 指向 **中斷點**，然後按一下**插入中斷點**。

6.  按一下**偵錯 XSL** XML 編輯器工具列上的按鈕。

這會啟動偵錯處理，並開啟偵錯工具所使用的幾個新視窗。

顯示輸入文件與樣式表的視窗有兩個。 偵錯工具會使用這些視窗來顯示目前的執行狀態。 偵錯工具位於`xsl:if`元素的樣式表和中的第一個書籍節點上*books.xml*檔案。

**區域變數**視窗會顯示所有的本機變數和其目前值。 其中包括在樣式表中定義的變數，及偵錯工具用來追蹤目前內容中之節點的變數。

**XSL 輸出**視窗會顯示 XSL 轉換的輸出。 此視窗是分開**Visual Studio 輸出**視窗。

## <a name="watch-window"></a>監看式視窗

### <a name="to-use-the-watch-window"></a>使用 [監看式] 視窗

1.  從**偵錯**功能表上，指向**Windows**，指向 **監看式**，然後按一下**監看式 1**。

     這可讓**監看式 1**可見的視窗。

2.  型別`$bookAverage`中**名稱**欄位，然後按**Enter**。

     `$bookAverage` 變數的值會顯示於視窗中。

3.  型別`self::node()`中**名稱**欄位，然後按**Enter**。

     `self::node()` 是一種 XPath 運算式，可評估目前的內容節點。 `self::node()` XPath 運算式的值為第一個書籍節點。 它會隨著轉換的進行而變更。

4.  展開 `self::node()` 節點，然後展開 `price` 節點。

     這樣可讓您查看書籍價格的值，而且可以輕鬆將其與 `$bookAverage` 值進行比較。 因為書籍價格低於平均值，所以 `xsl:if` 條件應該會成功。

## <a name="step-through-the-code"></a>逐步執行程式碼
 偵錯工具可讓您逐行執行程式碼。

### <a name="to-step-through-the-code"></a>逐步執行程式碼

1.  按 **F5** 繼續。

     因為第一個書籍節點滿足`xsl:if`條件，該書籍節點加入至**XSL 輸出**視窗。 偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。 偵錯工具現在定中的第二個書籍節點上*books.xml*檔案。

     在**監看式 1**視窗`self::node()`值變更為第二個書籍節點。 藉由檢查價格項目的值，您可以確定價格高於平均值，因此 `xsl:if` 條件應該會失敗。

2.  按 **F5** 繼續。

     因為不符合第二個書籍節點`xsl:if`條件，該書籍節點不會加入至**XSL 輸出**視窗。 偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。 偵錯工具現在位於第三個`book`節點*books.xml*檔案。

     在**監看式 1**視窗`self::node()`值變更為第三個書籍節點。 藉由檢查 `price` 項目的值，您可以確定價格低於平均值，因此 `xsl:if` 條件應該會成功。

3.  按 **F5** 繼續。

     因為`xsl:if`已滿足條件，將第三本書加入至**XSL 輸出**視窗。 當處理過 XML 文件中的所有書籍後，偵錯工具會停止。

## <a name="sample-files"></a>範例檔案

逐步教學會使用下列兩個檔案。

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>另請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)