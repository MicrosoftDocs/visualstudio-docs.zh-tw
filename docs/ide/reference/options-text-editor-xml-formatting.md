---
title: 選項、文字編輯器、XML、格式化
description: 瞭解如何使用 XML 區段中的格式化頁面，來指定如何在 XML 檔中格式化元素和屬性。
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: b5e3674c955b229c4c517db5d1dab3d36830da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932315"
---
# <a name="options-text-editor-xml-formatting"></a>選項、文字編輯器、XML、格式化

使用 [格式化] 選項來指定如何將您 XML 文件中的項目和屬性格式化。 若要存取 XML 格式化選項，請選擇 [**工具**  >  **選項**  >  **文字編輯器**  >  **XML**]，然後選擇 [**格式化**]。

## <a name="attributes"></a>屬性

**保留手動屬性格式化**

不要重新格式化屬性。 這是預設設定。

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

**從剪貼簿貼上**

重新格式化從剪貼簿貼上的 XML 文字。

**完成結束標記時**

完成結束標記時重新格式化元素。

## <a name="mixed-content"></a>混合內容

**依預設，格式化混合內容。**

嘗試重新格式化混合內容，但是在 `xml:space="preserve"` 範圍中找到的內容除外。 這是預設設定。

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
