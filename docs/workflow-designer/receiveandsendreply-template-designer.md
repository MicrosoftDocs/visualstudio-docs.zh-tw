---
title: 工作流程設計工具 Receiveandsendreply 範本設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650027"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 樣板設計工具

**Receiveandsendreply**範本是用來建立一對預先設定的 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動。 活動是 <xref:System.Activities.Statements.Sequence> 活動的一部分，而且會在伺服器上以要求/回應訊息交換模式的一部分相互關聯。

## <a name="the-receiveandsendreply-template"></a>Receiveandsendreply 範本

新增**receiveandsendreply**範本會執行三項工作，除了使用 <xref:System.Activities.Statements.Sequence> 活動建立 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動之外：

- 設定 <xref:System.ServiceModel.Activities.Receive> 活動的 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 和 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 屬性。

- 將 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.Receive> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

- 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="use-the-receiveandsendreply-template-designer"></a>使用 Receiveandsendreply 範本設計工具

在 工具箱 的 **訊息** 分類中，存取  **receiveandsendreply**  活動設計**工具**。 **Receiveandsendreply**  活動設計工具可以從 **工具箱** 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處。 卸載活動設計工具會建立可使用 [**傳送**] 活動設計工具設定的 <xref:System.ServiceModel.Activities.Receive> 活動，以及可以使用 SendReplyToReceive 設計工具設定的相互關聯 <xref:System.ServiceModel.Activities.SendReply>。

如需使用**接收**設計工具來設定 <xref:System.ServiceModel.Activities.Receive> 活動的詳細資訊，請參閱[Receive 活動設計](../workflow-designer/receive-activity-designer.md)工具。

### <a name="properties-of-sendreply"></a>SendReply 的屬性

下表顯示 <xref:System.ServiceModel.Activities.SendReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在 [屬性] 方格中編輯，有些則可以在工作流程設計工具介面上編輯。

| 屬性名稱 | 必要項 | 使用量 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.SendReply> 活動可選用的易記名稱。 預設為 SendReplyToReceive。<br /><br /> 雖然不一定要使用易記 <xref:System.Activities.Activity.DisplayName%2A> 的非預設值，但最好是使用這種值。 |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | 參考到與這個 <xref:System.ServiceModel.Activities.Receive> 活動成對的 <xref:System.ServiceModel.Activities.SendReply> 活動。 這個屬性不得為**null**。 伺服器會同時使用 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動，以製作要求/回應傳訊模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您無法編輯這個屬性，因為它會自動系結至您建立 <xref:System.ServiceModel.Activities.SendReply> 活動的 <xref:System.ServiceModel.Activities.Send> 活動。 |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | 指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 按一下屬性方格中 [**內容**] 欄位旁的省略號按鈕，或按一下 [ **Receive** ] 活動設計工具介面上 [**內容**] 標籤旁的 [**定義**] 按鈕，即可編輯此屬性。 兩者都會顯示 [**內容定義**] 對話方塊。 如需如何使用此方塊的詳細資訊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。 |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | 指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下 [屬性] 方格中 [<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>] 屬性旁的省略號按鈕，以開啟 [**加入相互關聯初始化運算式**] 對話方塊。 如需使用此方塊的詳細資訊，請參閱[新增 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。 |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | 指定訊息的動作標頭。 如果未明確設定，其值會預設為：<br /><br /> <strong>https://tempuri.org/{service 合約命名空間}/合約名稱}/{作業名稱}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | 指定傳送回覆訊息前是否要保存工作流程執行個體。 預設值為 **false**。 |

## <a name="see-also"></a>請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)