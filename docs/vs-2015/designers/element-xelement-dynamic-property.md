---
title: Element (XElement 動態屬性) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7789a94c38f7c6d7db22d9214b19857e4c62055
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753883"
---
# <a name="element-xelement-dynamic-property"></a>Element (XElement 動態屬性)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

取得用於擷取對應於指定擴充名稱之子項目執行個體的索引子 (Indexer)。  
  
## <a name="syntax"></a>語法  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `XElement Item(String expandedName)` 型別的索引子。 如果沒有具有指定之名稱的項目，這個索引子會採用擴充名稱參數，並傳回對應的 <xref:System.Xml.Linq.XElement> 或 `null`。  
  
## <a name="remarks"></a>備註  
 這個屬性等同於 <xref:System.Xml.Linq.XContainer.Element%2A> 類別的 <xref:System.Xml.Linq.XContainer?displayProperty=fullName> 方法。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [項目](../designers/elements-xelement-dynamic-property.md)
