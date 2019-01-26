---
title: 格式化、XML、文字編輯器 (選項對話方塊)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5fbc4678431cd8b540b5bbc90bfab5dc2bb2bd4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020785"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>格式、 XML、 文字編輯器、 選項對話方塊

此對話方塊可讓您指定 XML 編輯器的格式化設定。 您可以存取**選項**對話方塊中，從**工具**功能表。

> [!NOTE]
> 這些設定都是當您選取**文字編輯器**資料夾中， **XML**資料夾，然後**格式化**選項**選項**  對話方塊。

## <a name="attributes"></a>屬性
 **保留手動屬性的格式**

 不重新格式化屬性。 這是預設值。

> [!NOTE]
> 如果屬性跨多行，則編輯器會將屬性的每一行縮排，以符合父項目的縮排。

 **將每個屬性在各自的行上對齊**

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

 結束標記完成時重新格式化項目。

## <a name="mixed-content"></a>混合的內容
 **依預設保留混合的內容**

 決定編輯器是否重新格式化混合內容。 依預設，編輯器嘗試重新格式化混合內容，內容在 `xml:space="preserve"` 範圍中時除外。

 如果項目包含文字與標記的混合，則將內容視為混合內容。 以下是具有混合內容的項目範例。

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>另請參閱

- [屬性視窗、 XML 文件屬性](../xml-tools/xml-document-properties-properties-window.md)
- [XML 編輯器元件](../xml-tools/xml-editor-components.md)