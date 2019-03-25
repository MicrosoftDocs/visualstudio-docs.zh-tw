---
title: 偵錯 XSLT 樣式表
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526629"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>逐步解說：偵錯 XSLT 樣式表

此逐步教學中的步驟示範如何使用 XSLT 偵錯工具。 這些步驟包括檢視變數、設定中斷點及逐步執行程式碼。 偵錯工具可讓您一次執行一行程式碼。

若要準備此逐步解說中，第一次複製這兩個[範例檔案](#sample-files)到本機電腦。 一個是樣式表中，一個是我們將使用做為輸入至樣式表的 XML 檔案。 在本逐步解說中，我們使用的樣式表會尋找其成本會低於書籍價格平均值的所有書籍。

> [!NOTE]
> 只有 Enterprise 版的 Visual Studio 中使用 XSLT 偵錯工具。

## <a name="start-debugging"></a>開始偵錯

1. 從**檔案**功能表上，選擇**開放** > **檔案**。

2. 找出*以下 average.xsl*檔案，然後選擇**開啟**。

   XML 編輯器中開啟樣式表。

3. 按一下 瀏覽按鈕 (**...**) 上**輸入**文件的 屬性 視窗的欄位。 (如果**屬性**看不到視窗，在編輯器中，開啟的檔案上按一下滑鼠右鍵，然後選擇**屬性**。)

4. 找出*books.xml*檔案，然後再選擇**開啟**。

   這會設定用於 XSLT 轉換的來源文件檔案。

5. 設定[中斷點](../debugger/using-breakpoints.md)在第 12 個行*以下 average.xsl*。 您可以在下列幾種方式：

   - 按一下第 12 行上的編輯器 的邊界。

   - 在第 12 行上任何位置按一下，然後按**F9**。

   - 以滑鼠右鍵按一下`xsl:if`開始標記，，然後選擇**中斷點** > **插入中斷點**。

      ![在 Visual Studio 中的 XSL 檔案中插入中斷點](media/insert-breakpoint.PNG)

6. 在功能表列上選擇  **XML** > **啟動 XSLT 偵錯**(或按**Alt**+**F5**)。

   在偵錯的處理序啟動。

   在編輯器中，偵錯工具位於`xsl:if`樣式表的項目。 另一個名為的檔案*以下 average.xml*編輯器; 中開啟這是將會填入做為輸入檔中的每個節點的輸出檔*books.xml*處理。

   **自動變數**，**區域變數**，並**監看式 1**視窗會出現在 Visual Studio 視窗底部。 **區域變數**視窗會顯示所有本機變數和其目前值。 其中包括在樣式表中定義的變數，及偵錯工具用來追蹤目前內容中之節點的變數。

## <a name="watch-window"></a>監看式視窗

我們將新增兩個變數來**監看式 1**視窗，以便處理的輸入的檔時，我們可以檢查其值。 (您也可以使用**區域變數**來檢查值，如果您想要監看的變數是否已有的視窗。)

1. 從**偵錯**功能表上，選擇**Windows** > **監看式** > **監看式 1**。

   **監看式 1**視窗成為可見。

2. 型別`$bookAverage`中**名稱**欄位，然後再按**Enter**。

   值`$bookAverage`變數會顯示在**值**欄位。

3. 在下一行中，輸入`self::node()`中**名稱**欄位，然後再按**Enter**。

   `self::node()` 是一種 XPath 運算式，可評估目前的內容節點。 `self::node()` XPath 運算式的值為第一個書籍節點。 它會隨著轉換的進行而變更。

4. 依序展開`self::node()`節點，然後展開節點誰具有值是`price`。

   ![在 Visual Studio 中的 XSLT 偵錯期間監看式視窗](media/xslt-debugging-watch-window.png)

   您可以查看書籍價格目前書籍節點的值，並比較它`$bookAverage`值。 因為書籍價格低於平均值，`xsl:if`繼續偵錯程序時，條件應該會成功。

## <a name="step-through-the-code"></a>逐步執行程式碼

1. 按 **F5** 繼續。

   因為第一個書籍節點滿足`xsl:if`條件，該書籍節點加入至*下方 average.xml*輸出檔。 偵錯工具繼續執行，直到其再次定位於樣式表的 `xsl:if` 項目上為止。 偵錯工具目前位於第二個書籍節點上的位置*books.xml*檔案。

   在 [**監看式 1** ] 視窗中，`self::node()`值變更為第二個書籍節點。 藉由檢查價格項目的值，您可以確定價格高於平均值，因此 `xsl:if` 條件應該會失敗。

2. 按 **F5** 繼續。

   因為不符合第二個書籍節點`xsl:if`條件，該書籍節點不會加入至*下方 average.xml*輸出檔。 偵錯工具會繼續執行直到其再次定位於上`xsl:if`樣式表中的項目。 偵錯工具現在位於第三個`book`中的節點*books.xml*檔案。

   在 [**監看式 1** ] 視窗中，`self::node()`值變更為第三個書籍節點。 藉由檢查的值`price`項目，您可以判斷價格低於平均值。 `xsl:if`條件應該會成功。

3. 按 **F5** 繼續。

   因為`xsl:if`已滿足條件，將第三本書加入至*下方 average.xml*輸出檔。 當處理過 XML 文件中的所有書籍後，偵錯工具會停止。

## <a name="sample-files"></a>範例檔案

逐步教學會使用下列兩個檔案。

### <a name="below-averagexsl"></a>below-average.xsl

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