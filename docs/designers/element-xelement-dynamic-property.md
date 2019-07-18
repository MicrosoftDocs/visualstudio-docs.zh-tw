---
title: Element (XElement 動態屬性)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbd197082174bcd23ab6b47d64eb4eb0f7944ca2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845538"
---
# <a name="element-xelement-dynamic-property"></a>Element (XElement 動態屬性)

取得用於擷取對應於指定擴充名稱之子項目執行個體的索引子 (Indexer)。

## <a name="syntax"></a>語法

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

`XElement Item(String expandedName)` 型別的索引子。 如果沒有具有指定之名稱的項目，這個索引子會採用擴充名稱參數，並傳回對應的 <xref:System.Xml.Linq.XElement> 或 `null`。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XContainer.Element%2A> 類別的 <xref:System.Xml.Linq.XContainer?displayProperty=fullName> 方法。

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)
- [項目](../designers/elements-xelement-dynamic-property.md)