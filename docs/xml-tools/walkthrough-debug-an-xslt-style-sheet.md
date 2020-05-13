---
title: 調試 XSLT 樣式表
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301717"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>演練：調試 XSLT 樣式表

此逐步教學中的步驟示範如何使用 XSLT 偵錯工具。 這些步驟包括檢視變數、設定中斷點及逐步執行程式碼。 調試器允許您一次執行一行代碼。

為準備本演練，請先將兩個[示例檔](#sample-files)複製到本地電腦。 一個是樣式表，一個是我們將用作樣式表輸入的 XML 檔。 在本演練中，我們使用的樣式表可查找所有成本低於平均書本價格的書籍。

> [!NOTE]
> XSLT 調試器僅在 Visual Studio 的企業版中可用。

## <a name="start-debugging"></a>開始偵錯

1. 在 **"檔"** 功能表中，選擇 **"打開** > **檔**"。

2. 找到*低於平均水準.xsl*的檔，然後選擇 **"打開**"。

   樣式表將在 XML 編輯器中打開。

3. 按一下文件屬性視窗的 **"輸入"** 欄位上的瀏覽按鈕 （**...）。** （如果 **"屬性"** 視窗不可見，請按右鍵編輯器中打開檔上的任意位置，然後選擇 **"屬性**"。"

4. 找到*book.xml*檔，然後選擇 **"打開**"。

   這將設置用於 XSLT 轉換的來源文件檔。

5. 在*低於平均值.xsl*的第 12 行設置[中斷點](../debugger/using-breakpoints.md)。 您可以通過多種方式之一執行此操作：

   - 按一下第 12 行編輯器的邊距。

   - 按一下第 12 行的任意位置，然後按**F9**。

   - 按右鍵`xsl:if`起始標記，然後選擇"**插入中斷點** > **Insert Breakpoint**"。

      ![在視覺化工作室中的 XSL 檔中插入中斷點](media/insert-breakpoint.PNG)

6. 在功能表列上，選擇**XML** > **啟動 XSLT 調試**（或者，按**Alt**+**F5**）。

   調試過程開始。

   在編輯器中，調試器位於樣式表`xsl:if`的元素上。 另一個名為*低於平均值.xml*的檔將在編輯器中打開;這是將填充為輸入檔*書.xml*中的每個節點的輸出檔案。

   **"自動**"、**區域變數**和**監視 1**視窗顯示在視覺化工作室視窗的底部。 **"區域變數"** 視窗顯示所有區域變數及其當前值。 其中包括在樣式表中定義的變數，及偵錯工具用來追蹤目前內容中之節點的變數。

## <a name="watch-window"></a>監看式視窗

我們將向**Watch 1**視窗添加兩個變數，以便在處理輸入檔時檢查它們的值。 （如果要查看的變數已存在，也可以使用 **"區域變數"** 視窗檢查值。

1. 在**調試**功能表中，選擇**Windows** > **監視** > **1**。

   **"監視 1"** 視窗變得可見。

2. 鍵入`$bookAverage`**"名稱"** 欄位，**然後按**Enter 。

   `$bookAverage`變數的值顯示在 **"值"** 欄位中。

3. 在下一行中，鍵入`self::node()`**"名稱"** 欄位，**然後按**Enter 。

   `self::node()`是一個 XPath 運算式，用於計算到當前上下文節點。 `self::node()` XPath 運算式的值為第一個書籍節點。 它會隨著轉換的進行而變更。

4. 展開`self::node()`節點，然後展開值為 的節點`price`。

   ![在視覺化工作室中 XSLT 調試期間監看視窗](media/xslt-debugging-watch-window.png)

   您可以看到當前書籍節點的圖書價格值，並將其與`$bookAverage`該值進行比較。 由於帳面價格低於平均值，因此當您繼續`xsl:if`調試過程時，條件應該會成功。

## <a name="step-through-the-code"></a>單一步驟代碼

1. 按**F5**繼續。

   由於第一個圖書節點滿足`xsl:if`條件，因此圖書節點將添加到*低於平均值.xml*輸出檔案中。 偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。 調試器現在位於*book.xml*檔中的第二個書籍節點上。

   在 **"監視 1"** 視窗中`self::node()`，值將更改為第二個書籍節點。 藉由檢查價格項目的值，您可以確定價格高於平均值，因此 `xsl:if` 條件應該會失敗。

2. 按**F5**繼續。

   由於第二個書籍節點不符合條件`xsl:if`，因此不會將書籍節點添加到*低於平均值.xml*輸出檔案中。 調試器將繼續執行，直到它再次定位在樣式表中`xsl:if`的元素上。 調試器現在位於*book.xml*檔中`book`的第三個節點上。

   在 **"監視 1"** 視窗中`self::node()`，值將更改為第三個書籍節點。 通過檢查元素的值，`price`可以確定價格低於平均值。 條件`xsl:if`應成功。

3. 按**F5**繼續。

   由於`xsl:if`條件得到滿足，因此第三本書將添加到*低於平均值.xml*輸出檔案中。 當處理過 XML 文件中的所有書籍後，偵錯工具會停止。

## <a name="sample-files"></a>範例檔案

逐步教學會使用下列兩個檔案。

### <a name="below-averagexsl"></a>低於平均水準.

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
        <xsl:if test="price &lt; $bookAverage">
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
