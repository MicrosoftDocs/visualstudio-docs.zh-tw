---
title: ExistsInCollection &lt; T &gt; 活動設計工具
description: 瞭解如何使用工作流程設計工具中的 [ExistsInCollection] <T> 活動設計工具來建立和設定 ExistsInCollection <T> 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9012bb936c2a9a8944639458d4165e08f5e7081e
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995404"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T> 活動設計工具

**\<T> ExistsInCollection** 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.ExistsInCollection%601> 活動。

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection \<T> 活動

<xref:System.Activities.Statements.ExistsInCollection%601> 活動會判斷特定集合中是否有指定項目存在。

### <a name="using-the-existsincollectiont-activity-designer"></a>使用 ExistsInCollection \<T> 活動設計工具

[ **ExistsInCollection \<T>** ] 活動設計 **工具** 位於 [工具箱] 的 [**集合**] 類別中，若要存取，請按一下工作流程設計工具的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

[ **ExistsInCollection \<T>** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.ExistsInCollection%601> 活動，預設值 <xref:System.Activities.Activity.DisplayName%2A> 為 ExistsInCollection<Int32 \> 。  (根據預設， *TypeArgument* 為 **Int32**。 您可以在屬性方格中變更此值。 ) <xref:System.Activities.Activity.DisplayName%2A> 可以在 **ExistsInCollection<\> T** 活動設計工具的標頭中編輯該值，也可以在屬性方格的 [ **DisplayName** ] 方塊中編輯。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection \<T> 屬性

下表顯示 <xref:System.Activities.Statements.ExistsInCollection%601> 屬性，並描述如何在設計工具中使用這些屬性：

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.ExistsInCollection%601> 活動的易記名稱。 預設值為 ExistsInCollection<Int32 \> 。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|是|要在集合中尋找的專案 \<T> 。 此專案的類型為 *T*，其類型為 *TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|是|要在其中檢查項目是否存在的集合。 此集合的類型為 **ICollection<TypeArgument \> 。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|是|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這個 *TypeArgument* 類型設定為 **Int32**。 若要變更類型，請變更屬性方格中下拉式方塊的 *TypeArgument* 值。|
|<xref:System.Activities.Activity%601.Result%2A>|否|表示指定項目是否存在於集合的值。 若要指定繫結至結果的變數，請在屬性方格中輸入 Visual Basic 變數。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)