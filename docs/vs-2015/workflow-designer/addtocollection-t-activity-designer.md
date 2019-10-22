---
title: AddToCollection &lt;T &gt; 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659199"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection &lt;T &gt; 活動設計工具
[ **AddToCollection \<T >** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.AddToCollection%601> 活動。

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T > 活動
 <xref:System.Activities.Statements.AddToCollection%601> 活動會將項目加入至集合。

### <a name="using-the-addtocollectiont-activity-designer"></a>使用 AddToCollection \<T > 活動設計工具
 [ **AddToCollection \<T >** ] 活動設計工具位於 [**工具箱**] 的 [**集合**] 類別中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 的 [**工具箱**] 索引標籤（也可以選取 [**工具列**]，從[ **View** ] 功能表或 CTRL + ALT + X）。

 [ **AddToCollection \<T >** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立 <xref:System.Activities.Statements.AddToCollection%601> 活動，其預設 <xref:System.Activities.Activity.DisplayName%2A> 為 AddToCollection \<Int32 >。 （根據預設， *TypeArgument*為**Int32**。 這可以在屬性方格中變更）。@No__t_0 值可以在 [ **AddToCollection \<T >** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。 其他的屬性必須在屬性方格上進行編輯。

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T > 屬性
 下表顯示 <xref:System.Activities.Statements.AddToCollection%601> 屬性，並且描述屬性在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 活動的易記名稱。 預設值為 AddToCollection \<Int32 >。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|要加入至集合的專案 \<T >。 此專案的類型為*T*，其類型為*TypeArgument*。 若要指定項目，請在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|應該加入項目的集合。 這個集合的類型為**ICollection \<TypeArgument >** 。 若要指定集合，請在屬性方格中輸入 Visual Basic 運算式。|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> 所包含項目的 T 型別。 根據預設，此*TypeArgument*類型會設定為**Int32**。 若要變更類型，請在屬性方格的下拉式方塊中變更*TypeArgument*的值。|

## <a name="see-also"></a>請參閱
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T > 活動設計](../workflow-designer/addtocollection-t-activity-designer.md)工具[ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)