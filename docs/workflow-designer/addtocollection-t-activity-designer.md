---
title: "AddToCollection&lt;T&gt;活動設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6da9179de0402acc5fdbe9cb5cfe7c8dda3ba1a5
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt;活動設計工具
**AddToCollection\<T >**活動設計工具用來建立及設定<xref:System.Activities.Statements.AddToCollection%601>活動。

## <a name="the-addtocollectiont-activity"></a>AddToCollection < T\>活動
 <xref:System.Activities.Statements.AddToCollection%601> 活動會將項目加入至集合。

### <a name="using-the-addtocollectiont-activity-designer"></a>使用 AddToCollection\<T > 活動設計工具
 **AddToCollection\<T >**活動設計工具位於**集合**分類的**工具箱**，依序按一下存取的哪一個**工具箱** 索引標籤[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **AddToCollection\<T >**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>. 這會建立<xref:System.Activities.Statements.AddToCollection%601>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的 AddToCollection < Int32\>。 (根據預設， *TypeArgument*是**Int32**。 這可以在屬性方格中變更)。<xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**AddToCollection < T\>** 活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-addtocollectiont-properties"></a>AddToCollection < T\>屬性
 下表顯示 <xref:System.Activities.Statements.AddToCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活動的易記名稱。 預設值是 AddToCollection < Int32\>。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要加入至集合的項目\<T >。 此項目屬於型別*T*，類型*TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|應該加入項目的集合。 此集合屬於型別**ICollection < TypeArgument\>**。 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這*TypeArgument*類型設定為**Int32**。 若要變更的類型，將變更的值*TypeArgument*屬性方格中的下拉式方塊中。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > 活動設計工具](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)