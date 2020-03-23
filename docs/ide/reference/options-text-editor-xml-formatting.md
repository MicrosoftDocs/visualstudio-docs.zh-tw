---
title: 選項、文字編輯器、XML、格式化
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568135"
---
# <a name="options-text-editor-xml-formatting"></a>選項、文字編輯器、XML、格式化

使用 [格式化]**** 選項來指定如何將您 XML 文件中的項目和屬性格式化。 要訪問 XML 格式選項，請選擇**工具** > **選項** > **文字編輯器** > **XML，** 然後選擇 **"格式化**"。

## <a name="attributes"></a>屬性

**保留手動屬性格式化**

不要重新格式化屬性。 這項設定是預設值。

> [!NOTE]
> 如果屬性在多行中，編輯器就會縮排每一個屬性行，以符合父元素的縮排。

**在個別的行上對齊每一個屬性**

將第二個和後續的屬性垂直對齊，以符合第一個屬性的縮排。 下列 XML 文字為如何對齊屬性的範例：

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>自動重新格式化

**從剪貼簿粘貼**

重新格式化從剪貼簿貼上的 XML 文字。

**完成結束標記時**

完成結束標記時重新格式化元素。

## <a name="mixed-content"></a>混合內容

**依預設，格式化混合內容。**

嘗試重新格式化混合內容，但是在 `xml:space="preserve"` 範圍中找到的內容除外。 這項設定是預設值。

如果元素包含文字與標記的混合，則內容會被視為混合內容。 下列是具有混合內容之元素的範例。

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>另請參閱

- [XML 選項 - 其他](options-text-editor-xml-miscellaneous.md)
- [Visual Studio 中的 XML 工具](../../xml-tools/xml-tools-in-visual-studio.md)
