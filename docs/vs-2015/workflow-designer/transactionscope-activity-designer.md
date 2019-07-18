---
title: TransactionScope 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: abed15a1ce3d406cfd5e95318dd332a677f61095
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976545"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope 活動設計工具
**TransactionScope**活動設計工具會用來建立及設定<xref:System.Activities.Statements.TransactionScope>活動。  
  
## <a name="the-transactionscope-activity"></a>TransactionScope 活動  
 <xref:System.Activities.Statements.TransactionScope> 活動會以單一異動的方式執行其中包含的活動。 在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動及交易中所有其他參與者均順利完成之後，就會認可交易。  
  
### <a name="using-the-transactionscope-activity-designer"></a>使用 TransactionScope 活動設計工具  
 **TransactionScope**活動設計工具位於**交易**類別**工具箱**，即可存取的哪一個**工具箱**索引標籤[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **TransactionScope**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.TransactionScope> 活動，具有 TransactionScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**TransactionScope**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-transactionscope-properties"></a>TransactionScope 屬性  
 下表顯示 <xref:System.Activities.Statements.TransactionScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 與 <xref:System.Activities.Statements.TransactionScope.Body%2A> 屬性可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。 但其他屬性必須在屬性方格上進行編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> 活動可選用的易記名稱。 預設為 TransactionScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|指定要在單一交易中執行的活動。 新增<xref:System.Activities.Statements.TransactionScope.Body%2A>活動，從下拉式**工具箱**成**主體**方塊**TransactionScope**提示文字 「 在此置放活動的活動設計工具在這裡 」。|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|為這個 <xref:System.Transactions.IsolationLevel> 指定 <xref:System.Activities.Statements.TransactionScope>。|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|指定異動必須完成的時間間隔 (格式為 00:00:00，表示時:分:秒)。 預設值是 1 分鐘 (00:01:00)。|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|指定值，這個值會指出當交易中止時，工作流程是否應隨之中止。|  
  
## <a name="see-also"></a>另請參閱  
 [交易](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [補償](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)