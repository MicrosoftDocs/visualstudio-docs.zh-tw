---
title: AddToCollection&lt;T&gt;活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e63486ca7e057fdd1bfe0de73e44dc4951462e2
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58945301"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt;活動設計工具
**AddToCollection\<T >** 活動設計工具會用來建立及設定<xref:System.Activities.Statements.AddToCollection%601>活動。  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > 活動  
 <xref:System.Activities.Statements.AddToCollection%601> 活動會將項目加入至集合。  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>使用 AddToCollection\<T > 活動設計工具  
 **AddToCollection\<T >** 活動設計工具可在**集合**分類**工具箱**，依序按一下 存取的哪一個**工具箱**索引標籤[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **AddToCollection\<T >** 活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>. 這會建立<xref:System.Activities.Statements.AddToCollection%601>活動，具有預設值<xref:System.Activities.Activity.DisplayName%2A>AddToCollection 的\<Int32 >。 (根據預設， *TypeArgument*是**Int32**。 這可以在屬性方格中變更)。<xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**AddToCollection\<T >** 活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在屬性方格上進行編輯。  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > 屬性  
 下表顯示 <xref:System.Activities.Statements.AddToCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活動的易記名稱。 預設值是 AddToCollection\<Int32 >。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要加入至集合的項目\<T >。 此項目屬於類型*T*，這是型別的*TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|應該加入項目的集合。 此集合屬於類型**ICollection\<TypeArgument >**。 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這*TypeArgument*類型設定為**Int32**。 若要變更的類型，將變更的值*TypeArgument*下拉式方塊，在屬性方格中。|  
  
## <a name="see-also"></a>另請參閱  
 [集合](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > 活動設計工具](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)