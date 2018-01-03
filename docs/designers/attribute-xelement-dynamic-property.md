---
title: "Attribute (XElement 動態屬性) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3f373f4732aa80ac0e72f044e7a6a7f08e8a9be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (XElement 動態屬性)
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