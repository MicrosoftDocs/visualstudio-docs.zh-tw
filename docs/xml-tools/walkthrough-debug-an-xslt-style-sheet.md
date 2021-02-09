---
title: 調試 XSLT 樣式表單
description: 遵循本逐步解說中的步驟，瞭解如何使用 Visual Studio 中的 XSLT 偵錯工具，來對 XSLT 樣式表單進行 debug 錯。
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7935abf4bee4d7f9532ca1dfae0b7105c42067d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875155"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>逐步解說：偵錯 XSLT 樣式表

此逐步教學中的步驟示範如何使用 XSLT 偵錯工具。 這些步驟包括檢視變數、設定中斷點及逐步執行程式碼。 偵錯工具可讓您一次執行一行程式碼。

若要準備此逐步解說，請先將兩個 [範例](#sample-files) 檔案複製到本機電腦。 其中一個是樣式表單，而另一個是用來做為樣式表單輸入的 XML 檔。 在這個逐步解說中，我們使用的樣式表單會尋找其成本低於平均書籍價格的所有書籍。

> [!NOTE]
> XSLT 偵錯工具僅適用于 Visual Studio 的 Professional 和 Enterprise 版本。

## <a name="start-debugging"></a>開始偵錯

1. 選擇 [檔案 **] 功能表中的 [** **開啟** 檔案]  >  ****。

2. 找到 *below-average .xsl* 檔案，然後選擇 [ **開啟**]。

   樣式表單會在 XML 編輯器中開啟。

3. 按一下 [檔案屬性] 視窗中 [**輸入**] 欄位上的 [流覽] 按鈕 (**...**) 。  (如果看不到 [ **屬性** ] 視窗，請在編輯器中開啟之檔案的任何位置上按一下滑鼠右鍵，然後選擇 [ **屬性**]。 ) 

4. 找出 *books.xml* 檔案，然後選擇 [ **開啟**]。

   這會設定用於 XSLT 轉換的來源文件檔。

5. 在 *below-average* 的第12行上設定 [中斷點](../debugger/using-breakpoints.md)。 您可以透過下列其中一種方式來執行這項作業：

   - 在第12行的編輯器邊界中按一下。

   - 按一下第12行的任何位置，然後按 **F9**。

   - 以滑鼠右鍵按一下 [ `xsl:if` 開始] 標記，然後選擇 [**中斷點**  >  **插入中斷點**]。

      ![在 Visual Studio 中的 XSL 檔案插入中斷點](media/insert-breakpoint.PNG)

6. 在功能表列上，選擇 [ **XML**  >  **啟動 XSLT 調試** (]，或按下 **Alt** + **F5**) 。

   偵錯工具隨即啟動。

   在編輯器中，偵錯工具位於 `xsl:if` 樣式表單的元素上。 另一個名為 *below-average.xml* 的檔案會在編輯器中開啟;這是在處理輸入檔 *books.xml* 中的每個節點時，將填入的輸出檔。

   [自動變數]、[**區域變數**]**和 [****監看式 1]** 視窗會出現在 Visual Studio 視窗的底部。 [ **區域變數** ] 視窗會顯示所有區域變數和其目前的值。 其中包括在樣式表中定義的變數，及偵錯工具用來追蹤目前內容中之節點的變數。

## <a name="watch-window"></a>監看式視窗

我們會將兩個變數新增至 [ **監看式 1** ] 視窗，讓我們可以在處理輸入檔時檢查其值。  (如果您要監看的變數已經存在，您也可以使用 [ **區域變數** ] 視窗檢查值。 ) 

1. 在 [**調試**] 功能表中，選擇 [ **Windows**  >  **watch**  >  **watch 1]**。

   [ **監** 看式 1] 視窗隨即顯示。

2. `$bookAverage`在 [**名稱**] 欄位中輸入，然後按 **enter**。

   變數的值會 `$bookAverage` 顯示在 [ **值** ] 欄位中。

3. 在下一行中，輸入 `self::node()` [ **名稱** ] 欄位，然後按 **enter**。

   `self::node()` 這是評估為目前內容節點的 XPath 運算式。 `self::node()` XPath 運算式的值為第一個書籍節點。 它會隨著轉換的進行而變更。

4. 展開 `self::node()` 節點，然後展開其值為的節點 `price` 。

   ![在 Visual Studio 的 XSLT 調試期間監看式視窗](media/xslt-debugging-watch-window.png)

   您可以查看目前書籍節點的書籍價格值，並將其與值進行比較 `$bookAverage` 。 由於書籍價格低於平均值，因此 `xsl:if` 當您繼續進行偵錯工具時，條件應該會成功。

## <a name="step-through-the-code"></a>逐步執行程式碼

1. 按 **F5** 繼續。

   因為第一個書籍節點滿足 `xsl:if` 條件，所以會將 book 節點新增至 *below-average.xml* 輸出檔。 偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。 偵錯工具現在位於 *books.xml* 檔案的第二個書籍節點上。

   在 [ **監看式 1** ] 視窗中， `self::node()` 值會變更為第二個書籍節點。 藉由檢查價格項目的值，您可以確定價格高於平均值，因此 `xsl:if` 條件應該會失敗。

2. 按 **F5** 繼續。

   因為第二個書籍節點不符合 `xsl:if` 條件，所以不會將 [書籍] 節點新增至 *below-average.xml* 輸出檔。 偵錯工具會繼續執行，直到它再次放置於 `xsl:if` 樣式表單中的元素上為止。 偵錯工具現在位於books.xml檔案的第三個 `book` 節點上。

   在 [ **監看式 1** ] 視窗中， `self::node()` 值會變更為第三個書籍節點。 藉由檢查項目的值 `price` ，您可以判斷價格低於平均值。 `xsl:if`條件應該會成功。

3. 按 **F5** 繼續。

   因為 `xsl:if` 已滿足條件，所以會將第三本書新增至 *below-average.xml* 輸出檔。 當處理過 XML 文件中的所有書籍後，偵錯工具會停止。

## <a name="sample-files"></a>範例檔案

逐步教學會使用下列兩個檔案。

### <a name="below-averagexsl"></a>below-average .xsl

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
