---
title: 工作流設計器 - 發送和接收回複範本設計器
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395251"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 樣本設計工具

**SendAndReceiveReply**範本用於創建一對預配置<xref:System.ServiceModel.Activities.Send>的活動。 <xref:System.ServiceModel.Activities.ReceiveReply> 活動是活動的一<xref:System.Activities.Statements.Sequence>部分，並作為用戶端上的請求/回應訊息交換模式的一部分進行關聯。

## <a name="the-sendandreceivereply-template"></a>發送和接收回複範本

添加**SendAndReceiveReply**範本除了在<xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply><xref:System.Activities.Statements.Sequence>活動中創建 和 活動外，還有三件事：

- 配置<xref:System.ServiceModel.Activities.Send.OperationName%2A><xref:System.ServiceModel.Activities.Send>活動的 和<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>屬性。

- 將 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

- 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="use-the-sendandreceivereply-template-designer"></a>使用發送和接收回複範本設計器

訪問**工具箱****"消息"** 類別中的 **"發送和接收回複"** 活動設計器。 **SendAndReceiveReply**活動設計器可以從**工具箱**拖動，並放置在工作流設計器表面上，無論活動通常放置在哪裡。 刪除活動設計器將創建<xref:System.ServiceModel.Activities.Send>一個活動，該活動可以使用 **"發送"** 活動設計器<xref:System.ServiceModel.Activities.ReceiveReply>配置，並創建一個可以使用**ReceiveReplyForSend**設計器配置的相關活動。

有關使用 **"發送**設計器"配置<xref:System.ServiceModel.Activities.Send>活動的詳細資訊，請參閱[發送](../workflow-designer/send-activity-designer.md)。

### <a name="properties-of-receivereply"></a>ReceiveReply 的屬性

下表顯示了屬性，<xref:System.ServiceModel.Activities.ReceiveReply>並描述了它們在設計器中的使用方式。 這些屬性可以在屬性網格中編輯，有些可以在工作流設計器表面上進行編輯。

| 屬性名稱 | 必要 | 使用量 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.ReceiveReply> 活動可選用的易記名稱。 預設為 ReceiveReplyForSend。<br /><br /> 儘管不是嚴格要求對友好值<xref:System.Activities.Activity.DisplayName%2A>使用非預設值，但最好使用這樣的值。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | 參考到與這個 <xref:System.ServiceModel.Activities.Send> 活動成對的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 此屬性不能**為 null**。 <xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>活動一起使用在用戶端上建模請求/回應訊息傳遞模式。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計器中，無法編輯此屬性，因為它會自動綁定到您從中創建活動<xref:System.ServiceModel.Activities.Send>的活動。 <xref:System.ServiceModel.Activities.ReceiveReply> |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | 指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 通過按一下屬性網格中 **"內容"** 欄位旁邊的省略號按鈕，或按一下 **"接收**活動設計器"圖名圖人曲面上 **"內容**"標籤旁邊的 **"定義"** 按鈕來編輯此屬性。 兩者都顯示 **"內容定義"** 對話方塊。 有關如何使用此框的詳細資訊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | 指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下屬性網格中<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>屬性旁邊的省略號按鈕以打開"**添加關聯初始化器"** 對話方塊。 有關使用此框的詳細資訊，請參閱[添加關聯初始程式對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | 指定訊息的動作標頭。 如果未顯式設置，則其值預設為：<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [收到](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [發送](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)