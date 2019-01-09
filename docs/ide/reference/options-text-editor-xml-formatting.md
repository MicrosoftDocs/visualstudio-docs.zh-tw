---
title: 選項、文字編輯器、XML、格式化
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0d8420df205d49df3c6799e62adbc4e759a4aed2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826516"
---
# <a name="options-text-editor-xml-formatting"></a>選項、文字編輯器、XML、格式化

使用 [格式化] 屬性頁來指定如何格式化您 XML 文件中的項目和屬性。 若要開啟 [選項] 對話方塊，請按一下 [工具] 功能表，然後按一下 [選項]。 若要存取 [格式化] 屬性頁，請展開 [文字編輯器] > [XML] > [格式化] 節點。

## <a name="attributes"></a>屬性

**保留手動屬性的格式**

不要將屬性重新格式化。 此設定為預設。

> [!NOTE]
> 如果屬性跨多行，則編輯器會將屬性的每一行縮排，以符合父項目的縮排。

**對齊位於各行上的屬性**

垂直對齊第二個屬性及後續屬性，使其符合第一個屬性的縮排。 下列 XML 文字為如何對齊屬性的範例。

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>自動重新格式化

**從剪貼簿貼上**

重新格式化從剪貼簿貼上的 XML 文字。

**結束標記完成**

結束標記完成時將項目重新格式化。

## <a name="mixed-content"></a>混合內容

**根據預設，會將混合內容重新設定。**

會嘗試將混合內容重新格式化，但內容在 `xml:space="preserve"` 範圍中時除外。 此設定為預設。

如果項目包含文字與標記的混合，則將內容視為混合內容。 下列是具有混合內容的項目範例。

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>另請參閱

- [如何：建立 XML 文件 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [程式碼產生](../code-generation-in-visual-studio.md)