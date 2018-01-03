---
title: "Element (XElement 動態屬性) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ec02b03188ea0fd1fa7c15ea03878bdec12890f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="element-xelement-dynamic-property"></a>Element (XElement 動態屬性)
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