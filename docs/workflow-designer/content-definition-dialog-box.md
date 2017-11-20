---
title: "內容定義對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa0276e284f84eb6514fc407c9ce9be9cf24d8c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="content-definition-dialog-box"></a>內容定義對話方塊
**內容定義**對話方塊用於[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]設定**內容**屬性<xref:System.ServiceModel.Activities.Send>， <xref:System.ServiceModel.Activities.Receive>， <xref:System.ServiceModel.Activities.SendReply>，和<xref:System.ServiceModel.Activities.ReceiveReply>活動。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此方塊中，活動設計工具請參閱[傳送](../workflow-designer/send-activity-designer.md)，[接收](../workflow-designer/receive-activity-designer.md)， [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)，和[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)主題。  
  
 下表描述的使用者介面 (UI) 項目**初始化相互關聯** 對話方塊。  
  
|UI 項目|說明|  
|----------------|-----------------|  
|**訊息**|指定訊息內容與**訊息資料**運算式文字方塊中，使用型別**訊息類型**下拉式清單方塊。 根據預設，**內容定義**使用<xref:System.ServiceModel.Activities.ReceiveMessageContent>，這會預期<xref:System.ServiceModel.Channels.Message>或訊息合約中的工作流程服務定義的類型。|  
|**參數**|按一下**參數**選項按鈕，以使用<xref:System.ServiceModel.Activities.ReceiveParametersContent>，這會預期的資料合約。 使用資料方格設定 <xref:System.Activities.OutArgument> 索引鍵/值配對的泛型集合，配對的值會指派給目前工作流程中的變數參數。|  
  
 **內容定義**對話方塊由**傳送**，**接收**， **ReceiveAndSendReply**，和**SendAndReceiveReply**設計工具。 各種情況的存取方式很類似，在此使用 [Receive] 為例，以說明這個程序。  
  
 **接收**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取**接收**活動設計工具，然後按一下省略符號按鈕 （內容） 文字旁邊**內容**屬性方格中的**內容定義**對話方塊出現。  
  
 可以在指定的內容**訊息**區段<xref:System.ServiceModel.Activities.ReceiveMessageContent>活動或**參數**區段<xref:System.ServiceModel.Activities.ReceiveParametersContent>活動。  
  
## <a name="see-also"></a>另請參閱  
 [工作流程設計工具 UI 說明](../workflow-designer/workflow-designer-ui-help.md)