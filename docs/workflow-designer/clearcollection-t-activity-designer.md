---
title: 工作流程設計工具 ClearCollection <T> 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96f0b56172684c5c82910b34f40aa44fd6aec81
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876173"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T> 活動設計工具

[ **ClearCollection \<T> ** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.ClearCollection%601> 活動。

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T> 活動

<xref:System.Activities.Statements.ClearCollection%601> 活動會清除所有項目的指定集合。

### <a name="using-the-clearcollectiont-activity-designer"></a>使用 ClearCollection \<T> 活動設計工具

[ **ClearCollection \<T> ** ] 活動設計**工具**位於 [工具箱] 的 [**集合**] 類別中，若要存取，請按一下工作流程設計工具的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表中選取 [**工具箱**]，或按**Ctrl** + **Alt** + **X**。

[ **ClearCollection \<T> ** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載活動設計工具會建立一個 <xref:System.Activities.Statements.ClearCollection%601> 活動，其預設值為 <xref:System.Activities.Activity.DisplayName%2A> ClearCollection<Int32 \> 。 （根據預設， *TypeArgument*為**Int32**。 TypeArgument 可以在屬性方格中變更）。此 <xref:System.Activities.Activity.DisplayName%2A> 值可以在 [ **ClearCollection<\> T** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T> 屬性

下表顯示 <xref:System.Activities.Statements.ClearCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.ClearCollection%601> 活動選用的易記名稱。 預設值為 ClearCollection<Int32 \> 。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|是|指定要清除項目的集合。 這個集合是 ICollection 類型** \<TypeArgument> 。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|是|指定 <xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，此*TypeArgument*類型會設定為**Int32**。 若要變更類型，請在屬性方格的下拉式方塊中變更*TypeArgument*的值。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)