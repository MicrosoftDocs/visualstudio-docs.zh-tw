---
title: 工作流程設計工具-TransactionScope 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07e3d971e72c433de6a5239538fa665b7661ec3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040849"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope 活動設計工具

**TransactionScope**活動設計工具會用來建立及設定<xref:System.Activities.Statements.TransactionScope>活動。

## <a name="the-transactionscope-activity"></a>TransactionScope 活動

<xref:System.Activities.Statements.TransactionScope> 活動會以單一交易的方式執行其中包含的活動。 在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活動及交易中所有其他參與者均順利完成之後，就會認可交易。

### <a name="using-the-transactionscope-activity-designer"></a>使用 TransactionScope 活動設計工具

存取權**TransactionScope**中的活動設計工具**交易**分類**工具箱**。 **TransactionScope**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.TransactionScope> 活動，具有 TransactionScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**TransactionScope**活動設計工具或**DisplayName**屬性方格的方塊。

### <a name="the-transactionscope-properties"></a>TransactionScope 屬性

下表顯示 <xref:System.Activities.Statements.TransactionScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A>和<xref:System.Activities.Statements.TransactionScope.Body%2A>屬性可以在工作流程設計工具介面上編輯。 但其他屬性必須在屬性方格上進行編輯。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> 活動可選用的易記名稱。 預設為 TransactionScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|指定要在單一異動中執行的活動。 新增<xref:System.Activities.Statements.TransactionScope.Body%2A>活動，從下拉式**工具箱**成**主體**方塊**TransactionScope**提示文字 「 在此置放活動的活動設計工具在這裡 」。|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|為這個 <xref:System.Transactions.IsolationLevel> 指定 <xref:System.Activities.Statements.TransactionScope>。|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|指定交易必須完成的時間間隔 (格式為 00:00:00，表示時:分:秒)。 預設值是 1 分鐘 (00:01:00)。|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|指定值，這個值會指出當異動中止時，工作流程是否應隨之中止。|

## <a name="see-also"></a>另請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)