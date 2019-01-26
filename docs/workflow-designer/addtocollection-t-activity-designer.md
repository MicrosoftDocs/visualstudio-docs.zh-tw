---
title: 工作流程設計工具-AddToCollection<T>活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc59628de24af3d0e4910f3ff566791a508127fe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953535"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > 活動設計工具

**AddToCollection\<T >** 活動設計工具會用來建立及設定<xref:System.Activities.Statements.AddToCollection%601>活動。

## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > 活動

<xref:System.Activities.Statements.AddToCollection%601> 活動會將項目加入至集合。

### <a name="using-the-addtocollectiont-activity-designer"></a>使用 AddToCollection\<T > 活動設計工具

**AddToCollection\<T >** 活動設計工具可在**集合**分類**工具箱**，依序按一下 [存取的哪一個**工具箱**的工作流程設計工具] 索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**AddToCollection\<T >** 活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，只要放置活動的例如在內<xref:System.Activities.Statements.Sequence>. 卸除**AddToCollection\<T >** 活動設計工具建立<xref:System.Activities.Statements.AddToCollection%601>活動，具有預設值<xref:System.Activities.Activity.DisplayName%2A>的 AddToCollection < Int32\>。 (根據預設， *TypeArgument*是**Int32**。 TypeArgument 可以變更屬性方格中。）<xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**AddToCollection < T\>** 活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > 屬性

下表顯示 <xref:System.Activities.Statements.AddToCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活動的易記名稱。 預設值是 AddToCollection < Int32\>。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要加入至集合的項目\<T >。 此項目屬於類型*T*，這是型別的*TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|應該加入項目的集合。 此集合屬於類型**ICollection < TypeArgument\>**。 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這*TypeArgument*類型設定為**Int32**。 若要變更的類型，將變更的值*TypeArgument*下拉式方塊，在屬性方格中。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > 活動設計工具](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)