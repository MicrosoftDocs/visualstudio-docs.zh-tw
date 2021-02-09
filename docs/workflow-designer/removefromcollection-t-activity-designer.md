---
title: RemoveFromCollection &lt; T &gt; 活動設計工具
description: 在工作流程設計工具中，您將瞭解如何使用 RemoveFromCollection <T> 活動設計工具來建立和設定 RemoveFromCollection <T> 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdaf7172c00d80e5e7615bfcadcc1fb6233c257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847358"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T> 活動設計工具

**\<T> RemoveFromCollection** 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.RemoveFromCollection%601> 活動。

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection \<T> 活動

<xref:System.Activities.Statements.RemoveFromCollection%601> 活動會移除某個特定集合中的指定項目。

### <a name="using-the-removefromcollectiont-activity-designer"></a>使用 RemoveFromCollection \<T> 活動設計工具

存取 [工具箱] 的 [**集合**] 類別中的 [ **RemoveFromCollection \<T>** ] 活動設計 **工具**。
[ **RemoveFromCollection \<T>** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.RemoveFromCollection%601> 活動，預設值 <xref:System.Activities.Activity.DisplayName%2A> 為 RemoveFromCollection<Int32 \> 。 您 <xref:System.Activities.Activity.DisplayName%2A> 可以在 **RemoveFromCollection<T \>** 活動設計工具的標頭中編輯此值，或在屬性方格的 [ **DisplayName** ] 方塊中編輯此值。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection<T \> 屬性

下表顯示 <xref:System.Activities.Statements.RemoveFromCollection%601> 屬性，並描述如何在設計工具中使用這些屬性：

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.RemoveFromCollection%601> 活動可選用的易記名稱。 預設值為 RemoveFromCollection<Int32 \> 。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|是|要從 **集合 \<T>** 中移除的專案。 此專案的類型為 *T*，其類型為 *TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|是|要從中移除專案的集合。 此集合的類型為 **ICollection<TypeArgument \> 。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|是|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這個 *TypeArgument* 類型設定為 **Int32**。 若要變更類型，請變更屬性方格中下拉式方塊的 *TypeArgument* 值。|
|<xref:System.Activities.Activity%601.Result%2A>|否|指出指定的項目是否可從集合內移除的值。 若要指定繫結至結果的變數，請在屬性方格中輸入變數。|

## <a name="see-also"></a>另請參閱

- [集合](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)