---
title: "加入 CorrelationInitializers 對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 4c4d8e07aa172aef524b4d85bda5ad8efdfb509f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="add-correlationinitializers-dialog-box"></a>加入相互關聯初始設定式對話方塊
**加入相互關聯初始設定式**對話方塊用於[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]設定**CorrelationInitializers**屬性<xref:System.ServiceModel.Activities.Send>， <xref:System.ServiceModel.Activities.Receive>， <xref:System.ServiceModel.Activities.SendReply>，和<xref:System.ServiceModel.Activities.ReceiveReply>活動。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用此方塊中，活動設計工具請參閱[傳送](../workflow-designer/send-activity-designer.md)，[接收](../workflow-designer/receive-activity-designer.md)， [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)，和[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)主題。  
  
 利用此對話方塊指定之集合中的相互關聯初始設定式，可以初始化傳訊活動之間以查詢為主、內容、回呼內容或要求-回覆的相互關聯。  
  
 下表描述的使用者介面 (UI) 項目**加入相互關聯初始設定式** 對話方塊。  
  
|UI 項目|描述|  
|----------------|-----------------|  
|**新增初始設定式**|按一下**新增初始化**方塊，以額外的初始設定式加入至集合。|  
|**相互關聯類型**|指定相互關聯初始設定式的型別。 有四個型別可供選擇：<br /><br /> 1.指定 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 的回呼相互關聯初始設定式。<br />2.指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 的內容相互關聯初始設定式。<br />3.指定 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 的要求-回覆相互關聯初始設定式。<br />4.指定 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 的查詢相互關聯初始設定式。<br /><br /> 若要編輯**相互關聯類型**<br /><br /> 1.索引標籤中的特定資料列**新增初始設定式**DataGrid。<br />2.按下 Ctrl + Tab 鍵將焦點設定**CorrelationTypeComboBox**<br />3.按 Alt + 向下快顯**ComboBox**並進行編輯。|  
|**XPath 查詢**|索引鍵/值組，其中包含用來從傳入與傳出訊息擷取相互關聯資料的查詢。 使用 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型別時，此清單才有效。|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>若要啟動加入相互關聯初始設定式對話方塊  
 **加入相互關聯初始設定式**對話方塊由**傳送**，**接收**， **ReceiveAndSendReply**，和**SendAndReceiveReply**設計工具。 存取方式很類似，在每個案例和案例，包括**接收**設計工具是使用以下說明這個程序。  
  
 **接收**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取**接收**活動設計工具，然後按一下省略符號按鈕 （集合） 文字旁邊**CorrelationInitializers**屬性方格中的**新增相互關聯初始設定式**對話方塊出現。  
  
## <a name="see-also"></a>請參閱  
 [加入相互關聯對話方塊](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)