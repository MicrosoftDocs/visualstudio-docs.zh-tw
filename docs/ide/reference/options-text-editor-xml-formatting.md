---
title: 選項、文字編輯器、XML、格式化
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e20b2f7ebe351aa050ea66468fb33aba8e4a31bc
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525065"
---
# <a name="options-text-editor-xml-formatting"></a>選項、文字編輯器、XML、格式化

使用 [格式化] 選項來指定如何將您 XML 文件中的項目和屬性格式化。 如果要存取 XML 格式化選項，請選擇 [工具] > [選項] > [文字編輯器] > [XML]，然後選擇 [格式化]。

## <a name="attributes"></a>屬性

**保留手動屬性的格式**

不要將屬性重新格式化。 此設定為預設。

> [!NOTE]
> 如果屬性跨多行，則編輯器會將屬性的每一行縮排，以符合父項目的縮排。

**對齊位於各行上的屬性**

垂直對齊第二個屬性及後續屬性，使其符合第一個屬性的縮排。 下列 XML 文字為如何對齊屬性的範例：

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

- [XML 選項 - 其他](options-text-editor-xml-miscellaneous.md)
- [Visual Studio 中的 XML 工具](../../xml-tools/xml-tools-in-visual-studio.md)