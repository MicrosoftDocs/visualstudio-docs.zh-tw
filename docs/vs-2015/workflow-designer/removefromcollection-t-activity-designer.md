---
title: RemoveFromCollection &lt; T &gt; 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672568"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection &lt; T &gt; 活動設計工具
** \<T> RemoveFromCollection**活動設計工具是用來建立及設定 <xref:System.Activities.Statements.RemoveFromCollection%601> 活動。

## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection \<T> 活動
 <xref:System.Activities.Statements.RemoveFromCollection%601> 活動會移除某個特定集合中的指定項目。

### <a name="using-the-removefromcollectiont-activity-designer"></a>使用 RemoveFromCollection \<T> 活動設計工具
 [ **RemoveFromCollection \<T> ** ] 活動設計**工具**位於 [工具箱] 的 [**集合**] 類別中，若要存取，請按一下 (上的 [**工具箱**] 索引標籤 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，或從 [ **View** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **RemoveFromCollection \<T> ** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.RemoveFromCollection%601> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32> 。 <xref:System.Activities.Activity.DisplayName%2A>值可以在 [ ** \<T> RemoveFromCollection** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection \<T> 屬性
 下表顯示 <xref:System.Activities.Statements.RemoveFromCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.RemoveFromCollection%601> 活動可選用的易記名稱。 預設值為 RemoveFromCollection \<Int32> 。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|是|要加入至**集合 \<T> **的專案。 此專案的類型為 *T*，其類型為 *TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|是|應該加入項目的集合。 此集合的類型為 **ICollection \<TypeArgument> 。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|是|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這個 *TypeArgument* 類型設定為 **Int32**。 若要變更類型，請變更屬性方格中下拉式方塊的 *TypeArgument* 值。|
|<xref:System.Activities.Activity%601.Result%2A>|否|指出指定的項目是否可從集合內移除的值。 若要指定繫結至結果的變數，請在屬性方格中輸入變數。|

## <a name="see-also"></a>另請參閱
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md)