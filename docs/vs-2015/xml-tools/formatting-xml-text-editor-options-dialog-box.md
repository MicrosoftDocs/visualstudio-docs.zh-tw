---
title: 選項對話方塊、文字編輯器、格式化、XMLMicrosoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670977"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>格式化、XML、文字編輯器 (選項對話方塊)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此對話方塊允許您指定 XML 編輯器的格式化設定。 您可以從 [工具]**** 功能表存取 [選項]**** 對話方塊。

> [!NOTE]
> 在選取 [文字編輯器]**** 資料夾、[XML]**** 資料夾，然後從 [選項]**** 對話方塊中選取 [格式化]**** 選項時，均可以使用這些設定。

## <a name="attributes"></a>屬性
 **保留手動屬性格式化** 屬性不會重新格式化。 這是預設值。

> [!NOTE]
> 如果屬性在多行中，編輯器就會縮排每一個屬性行，以符合父元素的縮排。

 **在各自的行上對齊屬性** 垂直對齊第二個和後續的屬性，以符合第一個屬性的縮排。 下列 XML 文字是如何對齊屬性的範例。

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>自動重新格式化
 **從剪貼簿貼上** 重新格式化從剪貼簿貼上的 XML 文字。

 **結束標記完成時** 當結束標記完成時重新格式化元素。

## <a name="mixed-content"></a>混合內容
 **依預設保留混合內容** 判斷編輯器是否重新格式化混合內容。 依預設，編輯器嘗試重新格式化混合內容，內容在 `xml:space="preserve"` 範圍中時除外。

 如果元素包含文字與標記的混合，則內容會被視為混合內容。 以下是具有混合內容的項目範例。

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>另請參閱
 [Xml 文件屬性，屬性視窗](../xml-tools/xml-document-properties-properties-window.md) [XML 編輯器元件](../xml-tools/xml-editor-components.md)
