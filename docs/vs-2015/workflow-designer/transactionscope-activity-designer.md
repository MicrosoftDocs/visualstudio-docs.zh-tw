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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670180"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope 活動設計工具
**TransactionScope**活動設計工具是用來建立及設定 <xref:System.Activities.Statements.TransactionScope> 活動。

## <a name="the-transactionscope-activity"></a>TransactionScope 活動
 <xref:System.Activities.Statements.TransactionScope> 活動會以單一異動的方式執行其中包含的活動。 在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動及交易中所有其他參與者均順利完成之後，就會認可交易。

### <a name="using-the-transactionscope-activity-designer"></a>使用 TransactionScope 活動設計工具
 [ **TransactionScope** ] 活動設計工具位於 [**工具箱**] 的 [**交易**] 類別中，若要存取，請按一下 (的 [**工具箱**] 索引標籤，也可以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **TransactionScope** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.TransactionScope> 活動，具有 TransactionScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以在 [ **TransactionScope** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-transactionscope-properties"></a>TransactionScope 屬性
 下表顯示 <xref:System.Activities.Statements.TransactionScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 與 <xref:System.Activities.Statements.TransactionScope.Body%2A> 屬性可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。 但其他屬性必須在屬性方格上進行編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.TransactionScope> 活動可選用的易記名稱。 預設為 TransactionScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|是|指定要在單一交易中執行的活動。 若要加入 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動，請從 [**工具箱**] 將活動拖放到 [ **TransactionScope** ] 活動設計工具的 [內文] 方塊中，並**在 [在**此放置活動] 提示文字。|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|是|為這個 <xref:System.Transactions.IsolationLevel> 指定 <xref:System.Activities.Statements.TransactionScope>。|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|否|指定異動必須完成的時間間隔 (格式為 00:00:00，表示時:分:秒)。 預設值是 1 分鐘 (00:01:00)。|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|是|指定值，這個值會指出當交易中止時，工作流程是否應隨之中止。|

## <a name="see-also"></a>另請參閱
 [交易](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [補償](../workflow-designer/compensate-activity-designer.md)[確認](../workflow-designer/confirm-activity-designer.md)