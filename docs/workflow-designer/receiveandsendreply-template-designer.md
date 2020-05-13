---
title: 工作流設計器 - 接收和發送回復範本設計器
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
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395292"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 樣板設計工具

**"接收和發送回復"** 範本用於創建一對預配置<xref:System.ServiceModel.Activities.Receive>的活動。 <xref:System.ServiceModel.Activities.SendReply> 活動是活動的一<xref:System.Activities.Statements.Sequence>部分，並作為伺服器上的請求/回應訊息交換模式的一部分進行關聯。

## <a name="the-receiveandsendreply-template"></a>接收和發送回復範本

添加**ReceiveAndSendReply**範本除了創建 具有活動<xref:System.ServiceModel.Activities.Receive>的活動<xref:System.ServiceModel.Activities.SendReply>之外，還有<xref:System.Activities.Statements.Sequence>三件事：

- 配置<xref:System.ServiceModel.Activities.Receive.OperationName%2A><xref:System.ServiceModel.Activities.Receive>活動的 和<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>屬性。

- 將 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.Receive> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

- 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="use-the-receiveandsendreply-template-designer"></a>使用接收和發送回復範本設計器

訪問**工具箱****"消息"** 類別中的 **"接收和發送回復**"活動設計器。 **接收和發送回復**活動設計器可以從**工具箱**拖動，並放置在工作流設計器表面上，無論活動通常放置在哪裡。 刪除活動設計器將創建<xref:System.ServiceModel.Activities.Receive>一個活動，該活動可以使用 **"發送活動**設計器"<xref:System.ServiceModel.Activities.SendReply>配置，並創建一個可以使用 SendReplyToReceive 設計器配置的相關活動。

有關使用**接收**設計器配置<xref:System.ServiceModel.Activities.Receive>活動的詳細資訊，請參閱[接收活動設計器](../workflow-designer/receive-activity-designer.md)。

### <a name="properties-of-sendreply"></a>SendReply 的屬性

下表顯示 <xref:System.ServiceModel.Activities.SendReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性網格中編輯，有些可以在工作流設計器表面上進行編輯。

| 屬性名稱 | 必要 | 使用量 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.SendReply> 活動可選用的易記名稱。 預設為 SendReplyToReceive。<br /><br /> 儘管不是嚴格要求對友好值<xref:System.Activities.Activity.DisplayName%2A>使用非預設值，但最好使用這樣的值。 |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | 參考到與這個 <xref:System.ServiceModel.Activities.Receive> 活動成對的 <xref:System.ServiceModel.Activities.SendReply> 活動。 此屬性不能**為 null**。 <xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動一起使用在伺服器上建模請求/回應訊息傳遞模式。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計器中，無法編輯此屬性，因為它會自動綁定到您從中創建活動<xref:System.ServiceModel.Activities.Send>的活動。 <xref:System.ServiceModel.Activities.SendReply> |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | 指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 通過按一下屬性網格中 **"內容"** 欄位旁邊的省略號按鈕，或按一下 **"接收**活動設計器"圖名圖人曲面上 **"內容**"標籤旁邊的 **"定義"** 按鈕來編輯此屬性。 兩者都顯示 **"內容定義"** 對話方塊。 有關如何使用此框的詳細資訊，請參閱[內容定義對話方塊主題](../workflow-designer/content-definition-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | 指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下屬性網格中<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>屬性旁邊的省略號按鈕以打開"**添加關聯初始化器"** 對話方塊。 有關使用此框的詳細資訊，請參閱[添加關聯初始程式對話方塊主題](../workflow-designer/add-correlationinitializers-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | 指定訊息的動作標頭。 如果未顯式設置，則其值預設為：<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | 指定傳送回覆訊息前是否要保存工作流程執行個體。 預設值為 **false**。 |

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [收到](../workflow-designer/receive-activity-designer.md)
- [發送](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)