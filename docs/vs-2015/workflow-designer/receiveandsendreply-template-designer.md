---
title: 接收和發送回復範本設計器 |微軟文檔
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395382"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 樣板設計工具
**ReceiveAndSendReply**範本用於在作為伺服器上的請求/回應訊息交換模式<xref:System.ServiceModel.Activities.Receive>的<xref:System.ServiceModel.Activities.SendReply>一<xref:System.Activities.Statements.Sequence>部分相關的活動中創建一對預配置的活動。

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 範本
 添加**ReceiveAndSendReply**範本除了創建 具有<xref:System.ServiceModel.Activities.Receive><xref:System.Activities.Statements.Sequence>活動<xref:System.ServiceModel.Activities.SendReply>的活動之外，還執行三件事：

1. 設定 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 活動的 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 與 <xref:System.ServiceModel.Activities.Receive> 屬性。

2. 將 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.Receive> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

3. 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="using-the-receiveandsendreply-template-designer"></a>使用 ReceiveAndSendReply 範本設計工具
 **"接收和發送回復**"活動設計器可在**工具箱****的消息**類別中找到，該類別可通過按一下[!INCLUDE[wfd2](../includes/wfd2-md.md)]中的 **"工具箱**"選項卡進行訪問（或者，從 **"視圖"** 功能表中選擇**工具列**或 CTRL_ALT_X）。

 **接收和發送回復**活動設計器可以從**工具箱**中拖動，並放置在通常放置活動的位置[!INCLUDE[wfd2](../includes/wfd2-md.md)]。 這將創建一<xref:System.ServiceModel.Activities.Receive>個可以使用 **"發送活動**"設計器配置的活動，以及可以使用<xref:System.ServiceModel.Activities.SendReply>SendReplyToReceive 設計器配置的相關活動。

 [!INCLUDE[crabout](../includes/crabout-md.md)]使用**接收**設計器配置<xref:System.ServiceModel.Activities.Receive>活動，請參閱[接收](../workflow-designer/receive-activity-designer.md)主題。

 [!INCLUDE[crabout](../includes/crabout-md.md)]使用**SendReplyTo 接收**設計器配置<xref:System.ServiceModel.Activities.SendReply>活動，請參閱以下部分。

### <a name="properties-of-sendreply"></a>SendReply 的屬性
 下表顯示 <xref:System.ServiceModel.Activities.SendReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|                               屬性名稱                                | 必要 |                                                                                                                                                                                                                                                                                                                                                      使用量                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.SendReply> 活動可選用的易記名稱。 預設為 SendReplyToReceive。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | 參考到與這個 <xref:System.ServiceModel.Activities.Receive> 活動成對的 <xref:System.ServiceModel.Activities.SendReply> 活動。 此屬性不能**為 null**。 <xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動一起使用在伺服器上建模請求/回應訊息傳遞模式。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.Send> 活動的 <xref:System.ServiceModel.Activities.SendReply> 活動。 |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 通過按一下屬性網格中 **"內容"** 欄位旁邊的橢圓按鈕或按一下 **"定義..."** **"接收**活動設計器"表面上**的內容**標籤旁邊的按鈕。 兩者都顯示 **"內容定義"** 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)]如何使用此框，請參閱[內容定義對話方塊主題](../workflow-designer/content-definition-dialog-box.md)。                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下屬性網格中<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>屬性旁邊的省略號按鈕以打開"**添加關聯初始化器"** 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)]使用此框，請參閱[添加關聯初始程式對話方塊主題](../workflow-designer/add-correlationinitializers-dialog-box.md)。            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              指定訊息的動作標頭。 如果沒有明確設定，其值會預設為：<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          指定傳送回覆訊息前是否要保存工作流程執行個體。 預設值為 **false**。                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>另請參閱
 [關聯範圍](../workflow-designer/correlationscope-activity-designer.md)[初始化相關](../workflow-designer/initializecorrelation-activity-designer.md)[接收](../workflow-designer/receive-activity-designer.md)[發送](../workflow-designer/send-activity-designer.md)[和接收回複](../workflow-designer/sendandreceivereply-template-designer.md)[處理接收範圍](../workflow-designer/transactedreceivescope-activity-designer.md)