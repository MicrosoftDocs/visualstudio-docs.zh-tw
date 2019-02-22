---
title: Attribute (XElement 動態屬性) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ced05b8da63f9a7a242b166fe64e9e44f78b8065
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776241"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (XElement 動態屬性)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

取得用於擷取對應於指定擴充名稱之屬性執行個體的索引子 (Indexer)。  
  
## <a name="syntax"></a>語法  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `XAttribute Item(String expandedName)` 型別的索引子。 如果沒有具有指定之名稱的屬性，這個索引子會採用指定之屬性的擴充名稱，並傳回對應的 <xref:System.Xml.Linq.XAttribute> 或 `null`。  
  
## <a name="remarks"></a>備註  
 這個屬性等同於 <xref:System.Xml.Linq.XElement.Attribute%2A> 類別的 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 方法。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xattribute-dynamic-property.md)
