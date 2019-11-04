---
title: Elements (XElement 動態屬性) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664685"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (XElement 動態屬性)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

取得用於擷取目前項目 (符合指定的擴充名稱) 之子項目的索引子 (Indexer)。

## <a name="syntax"></a>語法

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 `IEnumerable<XElement> Item(String expandedName)` 型別的索引子。 這個索引子會採用所需子項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。

## <a name="remarks"></a>備註
 這個屬性等同於 <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer> 方法。

 傳回集合中的項目順序為 XML 來源文件的順序。

 這個屬性會使用延後執行。

## <a name="see-also"></a>另請參閱
 [System.xml.linq.xelement> 類別動態屬性](../designers/xelement-class-dynamic-properties.md)[元素](../designers/element-xelement-dynamic-property.md) [子系](../designers/descendants-xelement-dynamic-property.md)
