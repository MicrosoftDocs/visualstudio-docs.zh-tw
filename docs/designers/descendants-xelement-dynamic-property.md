---
title: "Descendants (XElement 動態屬性) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a70d56be83a824c8bfd950ea148fe68e6ffa43b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (XElement 動態屬性)
取得用於擷取目前項目 (符合指定的擴充名稱) 之所有子代項目的索引子 (Indexer)。  
  
## <a name="syntax"></a>語法  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 `IEnumerable<XElement> Item(String expandedName)` 型別的索引子。 這個索引子會採用指定之子代項目的擴充名稱，並傳回 <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` 集合中相符的子項目。  
  
## <a name="remarks"></a>備註  
 這個屬性等同於 <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> 類別的 <xref:System.Xml.Linq.XContainer> 方法。  
  
 傳回集合中的項目順序為 XML 來源文件的順序。  
  
 這個屬性會使用延後執行。  
  
## <a name="see-also"></a>另請參閱  
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [項目](../designers/elements-xelement-dynamic-property.md)