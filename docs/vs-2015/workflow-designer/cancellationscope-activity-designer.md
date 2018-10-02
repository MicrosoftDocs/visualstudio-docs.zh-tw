---
title: CancellationScope 活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f8ddd5472a0e6540f8593c20e7f7d5735384f8e6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485632"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活動設計工具
**CancellationScope**活動設計工具會用來建立及設定<xref:System.Activities.Statements.CancellationScope>活動。  
  
## <a name="the-cancellationscope-activity"></a>CancellationScope 活動  
 <xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。  
  
### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活動設計工具  
 **CancellationScope**活動設計工具位於**交易**類別**工具箱**，即可存取的哪一個**工具箱**索引標籤[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **CancellationScope**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.CancellationScope> 活動，具有 CancellationScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**CancellationScope**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-cancellationscope-properties"></a>CancellationScope 屬性  
 下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。 預設為 CancellationScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定提供取消邏輯的活動。 若要新增<xref:System.Activities.Statements.CancellationScope.Body%2A>活動，從下拉式**工具箱**到**主體**方塊**CancellationScope**活動設計工具提示文字 「 卸除與活動 」。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定如果取消時所要執行的活動。 新增<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>活動，從下拉式**工具箱**成**已 CancellationHandler**方塊**CancellationScope**活動設計工具與提示文字"置放活動 」。|  
  
## <a name="see-also"></a>另請參閱  
 [交易](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [補償](../workflow-designer/compensate-activity-designer.md)   
 [確認](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)