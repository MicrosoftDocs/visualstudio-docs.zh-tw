---
title: ClearCollection &lt; T &gt; 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657015"
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection &lt; T &gt; 活動設計工具
** \<T> ClearCollection**活動設計工具是用來建立及設定 <xref:System.Activities.Statements.ClearCollection%601> 活動。

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T> 活動
 <xref:System.Activities.Statements.ClearCollection%601> 活動會清除所有項目的指定集合。

### <a name="using-the-clearcollectiont-activity-designer"></a>使用 ClearCollection \<T> 活動設計工具
 [ **ClearCollection \<T> ** ] 活動設計**工具**位於 [工具箱] 的 [**集合**] 類別中，若要存取，請按一下 (的 [**工具箱**] 索引標籤，也可以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 從 [ **View** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **ClearCollection \<T> ** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.ClearCollection%601> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> ClearCollection \<Int32> 。  (根據預設， *TypeArgument* 為 **Int32**。 這可以在屬性方格中變更。 ) <xref:System.Activities.Activity.DisplayName%2A> 可以在 [ **ClearCollection \<T> ** ] 活動設計工具的標頭中編輯此值，或在屬性方格的 [ **DisplayName** ] 方塊中編輯。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T> 屬性
 下表顯示 <xref:System.Activities.Statements.ClearCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.ClearCollection%601> 活動選用的易記名稱。 預設值為 ClearCollection \<Int32> 。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|是|指定要清除項目的集合。 此集合的類型為 **ICollection \<TypeArgument> 。** 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|是|指定 <xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，這個 *TypeArgument* 類型設定為 **Int32**。 若要變更類型，請變更屬性方格中下拉式方塊的 *TypeArgument* 值。|

## <a name="see-also"></a>另請參閱
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)