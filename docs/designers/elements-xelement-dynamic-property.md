---
title: Elements (XElement 動態屬性)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ff2071ba71d60db87332b0e23948d63ac1b2289
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913193"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (XElement 動態屬性)

取得用於擷取目前項目 (符合指定的擴充名稱) 之子項目的索引子 (Indexer)。

## <a name="syntax"></a>語法

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

`IEnumerable<XElement> Item(String expandedName)` 型別的索引子。 這個索引子會採用所需子項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer> 方法。

傳回集合中的項目順序為 XML 來源文件的順序。

這個屬性會使用延後執行。

## <a name="see-also"></a>另請參閱

- [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)
- [目](../designers/element-xelement-dynamic-property.md)
- [子系](../designers/descendants-xelement-dynamic-property.md)