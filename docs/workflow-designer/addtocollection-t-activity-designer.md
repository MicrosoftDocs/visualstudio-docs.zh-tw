---
title: AddToCollection &lt; T &gt; 活動設計工具
description: 瞭解如何使用 AddToCollection <T> 活動設計工具，在工作流程設計工具中建立和設定 AddToCollection <T> 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1592eab528f2312a9ad90dec02354814d6a81c3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993246"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T> 活動設計工具

**\<T> AddToCollection** 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.AddToCollection%601> 活動。

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T> 活動

<xref:System.Activities.Statements.AddToCollection%601> 活動會將項目加入至集合。

### <a name="using-the-addtocollectiont-activity-designer"></a>使用 AddToCollection \<T> 活動設計工具

[ **AddToCollection \<T>** ] 活動設計 **工具** 位於 [工具箱] 的 [**集合**] 類別中，若要存取，請按一下工作流程設計工具的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

[ **AddToCollection \<T>** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載 **AddToCollection \<T>** 活動設計工具會建立 <xref:System.Activities.Statements.AddToCollection%601> 預設為 <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32 的活動 \> 。  (根據預設， *TypeArgument* 為 **Int32**。 TypeArgument 可在屬性方格中變更。 ) <xref:System.Activities.Activity.DisplayName%2A> 可以在 **AddToCollection<\> T** 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯此值。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T> 屬性

下表顯示 <xref:System.Activities.Statements.AddToCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.AddToCollection%601> 活動的易記名稱。 預設值為 AddToCollection<Int32 \> 。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|是|要加入至集合的專案 \<T> 。 此專案的類型為 *T*，其類型為 *TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|是|應該加入項目的集合。 此集合的類型為 **ICollection<TypeArgument \>**。 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|是|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這個 *TypeArgument* 類型設定為 **Int32**。 若要變更類型，請變更屬性方格中下拉式方塊的 *TypeArgument* 值。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection \<T> 活動設計工具](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
