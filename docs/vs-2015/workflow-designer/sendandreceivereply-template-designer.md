---
title: 發送和接收回複範本設計器 |微軟文檔
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395330"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 樣本設計工具
**SendAndReceiveReply**範本用於在用戶端上作為請求/回應訊息交換<xref:System.ServiceModel.Activities.Send>模式<xref:System.ServiceModel.Activities.ReceiveReply>的一<xref:System.Activities.Statements.Sequence>部分相關的活動中創建一對預配置的活動。

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 範本
 添加**SendAndReceiveReply**範本除了在<xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply><xref:System.Activities.Statements.Sequence>活動中創建 和 活動之外，還執行三件事：

1. 設定 <xref:System.ServiceModel.Activities.Send.OperationName%2A> 活動的 <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> 與 <xref:System.ServiceModel.Activities.Send> 屬性。

2. 將 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

3. 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="using-the-sendandreceivereply-template-designer"></a>使用 SendAndReceiveReply 範本設計工具
 **SendAndReceiveReply**活動設計器可以在**工具箱****的消息**類別中找到，該類別可通過按一下"[!INCLUDE[wfd2](../includes/wfd2-md.md)]**工具箱**"選項卡進行訪問（或者，從 **"視圖"** 功能表中選擇**工具列**或 CTRL_ALT_X）。

 **SendAndReceiveReply**活動設計器可以從**工具箱**中拖動，並放置在[!INCLUDE[wfd2](../includes/wfd2-md.md)]通常放置活動的位置。 這將創建一<xref:System.ServiceModel.Activities.Send>個可以使用 **"發送活動"** 設計器配置的活動，以及可以使用<xref:System.ServiceModel.Activities.ReceiveReply> **ReceiveReplyForSend**設計器配置的相關活動。

 [!INCLUDE[crabout](../includes/crabout-md.md)]使用 **"發送**設計器"配置<xref:System.ServiceModel.Activities.Send>活動，請參閱["發送"](../workflow-designer/send-activity-designer.md)主題。

 [!INCLUDE[crabout](../includes/crabout-md.md)]使用**ReceiveReplyForSend**設計器配置<xref:System.ServiceModel.Activities.ReceiveReply>活動，請參閱以下部分。

### <a name="properties-of-receivereply"></a>ReceiveReply 的屬性
 下表顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|                                 屬性名稱                                 | 必要 |                                                                                                                                                                                                                                                                                                                                                        使用量                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.ReceiveReply> 活動可選用的易記名稱。 預設為 ReceiveReplyForSend。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | 參考到與這個 <xref:System.ServiceModel.Activities.Send> 活動成對的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 此屬性不能**為 null**。 <xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>活動一起使用在用戶端上建模請求/回應訊息傳遞模式。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.Send> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 通過按一下屬性網格中 **"內容"** 欄位旁邊的橢圓按鈕或按一下 **"定義..."** **"接收**活動設計器"表面上**的內容**標籤旁邊的按鈕。 兩者都顯示 **"內容定義"** 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)]如何使用此框，請參閱[內容定義對話方塊主題](../workflow-designer/content-definition-dialog-box.md)。                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下屬性網格中<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>屬性旁邊的省略號按鈕以打開"**添加關聯初始化器"** 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)]使用此框，請參閱[添加關聯初始程式對話方塊主題](../workflow-designer/add-correlationinitializers-dialog-box.md)。               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               指定訊息的動作標頭。 如果沒有明確設定，其值會預設為：<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>另請參閱
 [關聯範圍](../workflow-designer/correlationscope-activity-designer.md)[初始化相關](../workflow-designer/initializecorrelation-activity-designer.md)[接收](../workflow-designer/receive-activity-designer.md)[和發送回復](../workflow-designer/receiveandsendreply-template-designer.md)[發送](../workflow-designer/send-activity-designer.md)[轉接接收範圍](../workflow-designer/transactedreceivescope-activity-designer.md)