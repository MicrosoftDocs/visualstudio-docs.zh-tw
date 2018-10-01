---
title: Confirm 活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c65618a3b1961f0f686dddf84fdb42fee421a443
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486803"
---
# <a name="confirm-activity-designer"></a>Confirm 活動設計工具
**Confirm**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Confirm>活動。  
  
## <a name="the-confirm-activity"></a>Confirm 活動  
 <xref:System.Activities.Statements.Confirm> 活動會明確叫用包含在 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 中之活動的 <xref:System.Activities.Statements.CompensableActivity>。 如果 <xref:System.Activities.Statements.Confirm> 活動沒有在 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 之 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity> 的範圍內使用，您必須指定 <xref:System.Activities.Statements.Confirm.Target%2A> 屬性。  
  
 由 <xref:System.Activities.Statements.CompensationToken> 指定的 <xref:System.Activities.Statements.Compensate.Target%2A> 提供了一個方法，一旦 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 順利完成，即可明確確認或補償 <xref:System.Activities.Statements.CompensableActivity>。  
  
### <a name="using-the-confirm-activity-designer"></a>使用 Confirm 活動設計工具  
 **Confirm**活動設計工具可在**交易**類別**工具箱**，即可存取的哪一個**工具箱** 索引標籤上的左側[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **Confirm**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.Confirm> 活動，具有 Confirm 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以是標頭中編輯**確認**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-confirm-properties"></a>Confirm 屬性  
 下表顯示 <xref:System.Activities.Statements.Confirm> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯，但 <xref:System.Activities.Statements.Confirm.Target%2A> 屬性必須在屬性方格中編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.CancellationScope> 活動選用的易記名稱。 預設為 Confirm。|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，其中包含此 <xref:System.Activities.Statements.CompensationToken> 活動的 <xref:System.Activities.Statements.Confirm>。|  
  
## <a name="see-also"></a>另請參閱  
 [交易](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [補償](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)