---
title: TransactedReceiveScope 活動設計工具
description: 在工作流程設計工具中，您可以瞭解如何使用 TransactedReceiveScope 設計工具來建立和設定 TransactedReceiveScope 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9214d1ce4a873d6caea98b814e8d489f544944c5
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996288"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope 活動設計工具

**TransactedReceiveScope** 設計工具是用來建立及設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動。

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope 活動

<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可讓您將交易流動至工作流程或發送器建立的服務端交易。

### <a name="using-the-transactedreceivescope-activity-designer"></a>使用 TransactedReceiveScope 活動設計工具

存取 [工具箱] 的 [**訊息**] 類別中的 [ **TransactedReceiveScope** ] 活動設計 **工具**。 [ **TransactedReceiveScope** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處。 這會建立一個 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動，具有 TransactedReceiveScope 的預設 **DisplayName** 。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **TransactedReceiveScope** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

[ **TransactedReceiveScope** ] 設計工具組含 [ **要求** **] 和 [** 內文] 方塊。 這些會用來設定 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 屬性，而該屬性會指定 <xref:System.ServiceModel.Activities.Receive> 活動與 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 屬性，而此屬性再指定某個其他 <xref:System.Activities.Activity>。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 會建立異動。 然後，此異動會變成 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 範圍的環境異動，於是此範圍內的任何活動會在此異動的內部執行。

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope 屬性

下表顯示 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在工作流程設計工具介面上編輯，但其他屬性必須在設計介面上編輯。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動可選用的易記名稱。 預設為 TransactedReceiveScope。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 名稱並非絕對必要，但建議您盡量使用顯示名稱。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|是|將 <xref:System.ServiceModel.Activities.Receive> 活動放置到活動設計工具介面上的 **要求** 區塊。|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|否|<xref:System.Activities.Activity>將加入至活動設計工具介面上的 **主體** 區塊。|

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [收到](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)