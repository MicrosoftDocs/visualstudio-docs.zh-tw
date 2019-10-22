---
title: 工作流程設計工具-TransactionScope 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5d557fb91c52c33022a161bada169d4332bac6b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649825"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope 活動設計工具

[ **TransactionScope** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.TransactionScope> 活動。

## <a name="the-transactionscope-activity"></a>TransactionScope 活動

<xref:System.Activities.Statements.TransactionScope> 活動會以單一異動的方式執行其中包含的活動。 在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動及交易中所有其他參與者均順利完成之後，就會認可交易。

### <a name="using-the-transactionscope-activity-designer"></a>使用 TransactionScope 活動設計工具

在 [工具箱] 的 [**交易**] 類別中，存取 [ **TransactionScope** ] 活動設計**工具**。 [ **TransactionScope** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 這會建立一個 <xref:System.Activities.Statements.TransactionScope> 活動，具有 TransactionScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 您可以在 [ **TransactionScope** ] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。

### <a name="the-transactionscope-properties"></a>TransactionScope 屬性

下表顯示 <xref:System.Activities.Statements.TransactionScope> 屬性，並且描述屬性在設計工具中的使用方式。 @No__t_0 和 <xref:System.Activities.Statements.TransactionScope.Body%2A> 屬性可以在工作流程設計工具介面上編輯。 但其他屬性必須在屬性方格上進行編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> 活動可選用的易記名稱。 預設為 TransactionScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|指定要在單一交易中執行的活動。 若要加入 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動，請將活動從 [**工具箱**] 拖放到 [ **TransactionScope** ] 活動設計工具上**的 [內**文] 方塊中，並出現提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|為這個 <xref:System.Transactions.IsolationLevel> 指定 <xref:System.Activities.Statements.TransactionScope>。|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|指定異動必須完成的時間間隔 (格式為 00:00:00，表示時:分:秒)。 預設值是 1 分鐘 (00:01:00)。|
|[AbortInstanceOnTransactionFailure 的語句。](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|指定值，這個值會指出當交易中止時，工作流程是否應隨之中止。|

## <a name="see-also"></a>請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)