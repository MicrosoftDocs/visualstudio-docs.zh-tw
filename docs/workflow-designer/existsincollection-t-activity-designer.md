---
title: 工作流程設計工具-ExistsInCollection&lt;T&gt;活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06892bcfdca33e5e77e8c01f06f594849e5293e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949717"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > 活動設計工具

**ExistsInCollection\<T >** 活動設計工具會用來建立及設定<xref:System.Activities.Statements.ExistsInCollection%601>活動。

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > 活動

<xref:System.Activities.Statements.ExistsInCollection%601> 活動會判斷特定集合中是否有指定項目存在。

### <a name="using-the-existsincollectiont-activity-designer"></a>使用 ExistsInCollection\<T > 活動設計工具

**ExistsInCollection\<T >** 活動設計工具可在**集合**分類**工具箱**，依序按一下 [存取的哪一個**工具箱**的工作流程設計工具] 索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**ExistsInCollection\<T >** 活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.ExistsInCollection%601>活動，具有預設值<xref:System.Activities.Activity.DisplayName%2A>ExistsInCollection 的 < Int32\>。 (根據預設， *TypeArgument*是**Int32**。 它可以在屬性方格中變更)。<xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**ExistsInCollection < T\>** 活動設計工具或在**DisplayName**屬性方格的方塊。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > 屬性

下表顯示<xref:System.Activities.Statements.ExistsInCollection%601>內容並描述在設計工具的使用方式：

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ExistsInCollection%601> 活動的易記名稱。 預設值是 ExistsInCollection < Int32\>。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|要在集合中尋找的項目\<T >。 此項目屬於類型*T*，這是型別的*TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|集合中要檢查的項目是否存在。 此集合屬於類型**ICollection < TypeArgument\>。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這*TypeArgument*類型設定為**Int32**。 若要變更的類型，將變更的值*TypeArgument*下拉式方塊，在屬性方格中。|
|<xref:System.Activities.Activity%601.Result%2A>|False|表示指定項目是否存在於集合的值。 若要指定繫結至結果的變數，請在屬性方格中輸入 Visual Basic 變數。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)