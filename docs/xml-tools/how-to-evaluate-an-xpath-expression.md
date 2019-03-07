---
title: 評估 XPath 運算式在偵錯時
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526318"
---
# <a name="evaluate-xpath-expressions"></a>評估 XPath 運算式

您可以使用，以評估 XPath 運算式**快速監看式**偵錯期間的視窗。 根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。 目前的 XSLT 內容 (亦即`self::node()`中的節點**區域變數**視窗) 提供 XPath 運算式的評估內容。

當評估 XPath 運算式：

- 支援內建 XPath 函式。

- 不支援內建 XSLT 函式和使用者定義函式。

> [!NOTE]
> XSLT 偵錯僅供以 Visual Studio Enterprise 版。

## <a name="evaluate-an-xpath-expression"></a>評估 XPath 運算式

使用下列程序*average.xsl 如下*並*books.xml*檔案從[逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files)頁面。

1. 在 `xsl:if` 開始標記處插入中斷點。

2. 若要開始偵錯，請選擇**XML** > **啟動 XSLT 偵錯**功能表列上 (或按**Alt**+**F5**).

   偵錯工具會啟動，並在 `xsl:if` 標記處中斷。

3. 以滑鼠右鍵按一下並選取**快速監看式**。

   **快速監看式**視窗隨即開啟。

4. 請輸入`./price/text()`中**運算式**欄位**快速監看式**對話方塊的 []，然後選擇**重新評估**。

   目前書籍節點的價格會出現在**值** 方塊中。

   ![評估 XPath 運算式，在 [快速監看式] 視窗](media/quickwatch-price.png)

5. 將 XPath 運算式變更為`./price/text() < $bookAverage`，按一下 **重新評估**。

   **值** 方塊會顯示 XPath 運算式評估為`true`。

## <a name="see-also"></a>另請參閱

- [偵錯 XSLT](../xml-tools/debugging-xslt.md)