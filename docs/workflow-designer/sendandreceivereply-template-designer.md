---
title: SendAndReceiveReply 樣本設計工具
description: 瞭解如何在工作流程設計工具中使用 SendAndReceiveReply 範本來建立一對預先設定的傳送和 ReceiveReply 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02bcc4a812a541ea792a190dc21dfbeb3119c008
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943688"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 樣本設計工具

**SendAndReceiveReply** 範本是用來建立一對預先設定的 <xref:System.ServiceModel.Activities.Send> 與 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 活動是活動的一部分 <xref:System.Activities.Statements.Sequence> ，而且會在用戶端的要求/回應訊息交換模式中相互關聯。

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 範本

新增 **SendAndReceiveReply** 範本除了在 <xref:System.ServiceModel.Activities.Send> 活動中建立和活動之外，還會執行三件事 <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.Activities.Statements.Sequence> ：

- 設定 <xref:System.ServiceModel.Activities.Send.OperationName%2A> 活動的和 <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> 屬性 <xref:System.ServiceModel.Activities.Send> 。

- 將 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

- 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="use-the-sendandreceivereply-template-designer"></a>使用 SendAndReceiveReply 範本設計工具

存取 [工具箱] 的 [**訊息**] 類別中的 [ **SendAndReceiveReply** ] 活動設計 **工具**。 [ **SendAndReceiveReply** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處。 拖放活動設計工具時，會建立一個 <xref:System.ServiceModel.Activities.Send> 活動，該活動可以使用 [ **傳送** ] 活動設計工具和 <xref:System.ServiceModel.Activities.ReceiveReply> 可使用 **ReceiveReplyForSend** 設計工具設定的相互關聯來設定。

如需使用 **傳送** 設計工具來設定活動的詳細資訊 <xref:System.ServiceModel.Activities.Send> ，請參閱 [傳送](../workflow-designer/send-activity-designer.md)。

### <a name="properties-of-receivereply"></a>ReceiveReply 的屬性

下表顯示這些 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性，並描述它們在設計工具中的使用方式。 這些屬性可以在 [屬性] 方格中編輯，有些可以在工作流程設計工具介面上編輯。

| 屬性名稱 | 必要 | 使用方式 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | 否 | <xref:System.ServiceModel.Activities.ReceiveReply> 活動可選用的易記名稱。 預設為 ReceiveReplyForSend。<br /><br /> 雖然不是絕對需要使用非預設的易記值 <xref:System.Activities.Activity.DisplayName%2A> ，但最好是使用這類值。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | 是 | 參考到與這個 <xref:System.ServiceModel.Activities.Send> 活動成對的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 這個屬性不得為 **null**。 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動會一起用於用戶端上，以建立要求/回應訊息模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您無法編輯這個屬性，因為它會自動系結至 <xref:System.ServiceModel.Activities.Send> 您用來建立 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的活動。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | 否 | 指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 若要編輯這個屬性，請按一下屬性方格中 **[內容**] 欄位旁邊的省略號按鈕，或按一下 [ **Receive** ] 活動設計工具介面上 [**內容**] 標籤旁邊的 [**定義**] 按鈕。 兩者都會顯示 [ **內容定義** ] 對話方塊。 如需如何使用這個方塊的詳細資訊，請參閱 [ [內容定義] 對話方塊](../workflow-designer/content-definition-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | 否 | 指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下屬性方格中屬性旁邊的省略號按鈕， <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 以開啟 [加入相互 **關聯初始化運算式** ] 對話方塊。 如需使用此方塊的詳細資訊，請參閱 [加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | 否 | 指定訊息的動作標頭。 如果未明確設定，其值會預設為：<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [收到](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [發送](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)