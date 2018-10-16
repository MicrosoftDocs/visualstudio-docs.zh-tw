---
title: RemoveFromCollection&lt;T&gt;活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 341ed640666cc4501ac8917b568bf3f41b89b823
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170921"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection&lt;T&gt;活動設計工具
**RemoveFromCollection\<T >** 活動設計工具會用來建立及設定<xref:System.Activities.Statements.RemoveFromCollection%601>活動。  
  
## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection\<T > 活動  
 <xref:System.Activities.Statements.RemoveFromCollection%601> 活動會移除某個特定集合中的指定項目。  
  
### <a name="using-the-removefromcollectiont-activity-designer"></a>使用 RemoveFromCollection\<T > 活動設計工具  
 **RemoveFromCollection\<T >** 活動設計工具位於**集合**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **RemoveFromCollection\<T >** 活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面任一處通常用來放置活動，例如在<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.RemoveFromCollection%601>活動，具有預設值<xref:System.Activities.Activity.DisplayName%2A>RemoveFromCollection 的\<Int32 >。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**RemoveFromCollection\<T >** 活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在屬性方格上進行編輯。  
  
### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection\<T > 屬性  
 下表顯示 <xref:System.Activities.Statements.RemoveFromCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.RemoveFromCollection%601> 活動可選用的易記名稱。 預設值是 RemoveFromCollection\<Int32 >。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|要加入的項目**集合\<T >**。 此項目屬於類型*T*，這是型別的*TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|應該加入項目的集合。 此集合屬於類型**ICollection\<TypeArgument >。** 若要指定集合，請輸入在屬性方格中的 Visual Basic 運算式。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這*TypeArgument*類型設定為**Int32**。 若要變更的類型，將變更的值*TypeArgument*下拉式方塊，在屬性方格中。|  
|<xref:System.Activities.Activity%601.Result%2A>|False|指出指定的項目是否可從集合內移除的值。 若要指定繫結至結果的變數，請在屬性方格中輸入變數。|  
  
## <a name="see-also"></a>另請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)