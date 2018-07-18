---
title: 工作流程設計工具-ClearCollection<T>活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2422f7165e3f00e4059bc593c129c7723daed2f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757892"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > 活動設計工具

**ClearCollection\<T >** 活動設計工具會用來建立及設定<xref:System.Activities.Statements.ClearCollection%601>活動。

## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > 活動

<xref:System.Activities.Statements.ClearCollection%601> 活動會清除所有項目的指定集合。

### <a name="using-the-clearcollectiont-activity-designer"></a>使用 ClearCollection\<T > 活動設計工具

**ClearCollection\<T >** 活動設計工具可在**集合**分類**工具箱**，依序按一下 [存取的哪一個**工具箱**的工作流程設計工具] 索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**ClearCollection\<T >** 活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，只要放置活動的例如在內<xref:System.Activities.Statements.Sequence>. 卸除活動設計工具會建立<xref:System.Activities.Statements.ClearCollection%601>活動，具有預設值<xref:System.Activities.Activity.DisplayName%2A>ClearCollection 的 < Int32\>。 (根據預設， *TypeArgument*是**Int32**。 TypeArgument 可以變更屬性方格中。）<xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**ClearCollection < T\>** 活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > 屬性

下表顯示 <xref:System.Activities.Statements.ClearCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.ClearCollection%601> 活動選用的易記名稱。 預設值是 ClearCollection < Int32\>。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|指定要清除項目的集合。 此集合屬於類型**ICollection\<TypeArgument >。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|True|指定 <xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這*TypeArgument*類型設定為**Int32**。 若要變更的類型，將變更的值*TypeArgument*下拉式方塊，在屬性方格中。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)