---
title: 工作流程設計工具 TransactedReceiveScope 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf5a52a6a806d72632bf31a7c73e41677e9ddaf9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654283"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope 活動設計工具

**TransactedReceiveScope**設計工具是用來建立和設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動。

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope 活動

<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可讓您將交易流動至工作流程或發送器建立的服務端交易。

### <a name="using-the-transactedreceivescope-activity-designer"></a>使用 TransactedReceiveScope 活動設計工具

在 [工具箱] 的 [**訊息**] 分類中，存取 [ **TransactedReceiveScope** ] 活動設計**工具**。 [ **TransactedReceiveScope** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處。 這會建立具有 TransactedReceiveScope 預設**DisplayName**的 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動。 @No__t_0 可以在 [ **TransactedReceiveScope** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

**TransactedReceiveScope**設計工具組含 [要求 **] 和 [** 內文] 方塊。 這些會用來設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 屬性，而該屬性會指定 <xref:System.ServiceModel.Activities.Receive> 活動與 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 屬性，而此屬性再指定某個其他 <xref:System.Activities.Activity>。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 會建立異動。 然後，此異動會變成 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 範圍的環境異動，於是此範圍內的任何活動會在此異動的內部執行。

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope 屬性

下表顯示 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在工作流程設計工具介面上編輯，但其他則必須在設計介面上編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可選用的易記名稱。 預設為 TransactedReceiveScope。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 名稱並非絕對必要，但建議您盡量使用顯示名稱。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|將 <xref:System.ServiceModel.Activities.Receive> 活動拖放到活動設計工具介面上的**要求**區塊中。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|將 <xref:System.Activities.Activity> 放入活動設計工具介面上的**主體**區塊中。|

## <a name="see-also"></a>請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)