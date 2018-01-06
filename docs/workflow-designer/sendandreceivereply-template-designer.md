---
title: "SendAndReceiveReply 範本設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 314ff5252b426610b9a50327fe6754b2a953908c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 樣本設計工具
**SendAndReceiveReply**範本用來建立一對預先設定<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>內的活動<xref:System.Activities.Statements.Sequence>做為要求/回應訊息交換的一部分相互關聯的活動在用戶端上的模式。  
  
## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 範本  
 加入**SendAndReceiveReply**範本一樣三件事，除了建立<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>內的活動<xref:System.Activities.Statements.Sequence>活動：  
  
1.  設定 <xref:System.ServiceModel.Activities.Send.OperationName%2A> 活動的 <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> 與 <xref:System.ServiceModel.Activities.Send> 屬性。  
  
2.  將 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。  
  
3.  建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>使用 SendAndReceiveReply 範本設計工具  
 **SendAndReceiveReply**活動設計工具位於**傳訊**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **SendAndReceiveReply**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置。 這會建立<xref:System.ServiceModel.Activities.Send>活動，您可以使用設定**傳送**活動設計工具以及相互關聯<xref:System.ServiceModel.Activities.ReceiveReply>，您可以使用設定**ReceiveReplyForSend**設計工具。  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用**傳送**設計工具設定<xref:System.ServiceModel.Activities.Send>活動，請參閱[傳送](../workflow-designer/send-activity-designer.md)主題。  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用**ReceiveReplyForSend**設計工具設定<xref:System.ServiceModel.Activities.ReceiveReply>活動，請參閱下一節。  
  
### <a name="properties-of-receivereply"></a>ReceiveReply 的屬性  
 下表顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.ReceiveReply> 活動可選用的易記名稱。 預設為 ReceiveReplyForSend。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|參考到與這個 <xref:System.ServiceModel.Activities.Send> 活動成對的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 這個屬性不能**null**。 用戶端會同時使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動，以製作要求/回應傳訊模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.Send> 活動的來源 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 編輯這個屬性旁邊的橢圓形按鈕，即可**內容**在屬性方格，或按一下欄位**定義...**按鈕**內容**上加上標籤**接收**活動設計工具介面。 兩者都顯示**內容定義**對話方塊。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]如何使用此方塊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下省略符號按鈕旁的 [<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>屬性以開啟 [屬性] 方格中的**加入相互關聯初始設定式**] 對話方塊。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此方塊中，請參閱[加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|指定訊息的動作標頭。 如果沒有明確設定，其值會預設為：<br /><br /> **https://tempuri.org/ {服務合約命名空間} / {服務合約名稱} / {作業名稱}。**|  
  
## <a name="see-also"></a>請參閱  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [接收](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [傳送](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)