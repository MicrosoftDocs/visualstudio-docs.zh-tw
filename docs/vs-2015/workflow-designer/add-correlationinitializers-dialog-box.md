---
title: '[新增 CorrelationInitializers] 對話方塊 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672031"
---
# <a name="add-correlationinitializers-dialog-box"></a>加入相互關聯初始設定式對話方塊
[ **加入相互關聯初始化運算式** ] 對話方塊會在中用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 來設定、、和活動的 **CorrelationInitializers** 屬性 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> 。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊的活動設計工具，請參閱 [傳送](../workflow-designer/send-activity-designer.md)、 [接收](../workflow-designer/receive-activity-designer.md)、 [receiveandsendreply]](../workflow-designer/receiveandsendreply-template-designer.md)和 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 主題。

 利用此對話方塊指定之集合中的相互關聯初始設定式，可以初始化傳訊活動之間以查詢為主、內容、回呼內容或要求-回覆的相互關聯。

 下表描述 [ **加入相互關聯初始化運算式** ] 對話方塊中， (UI) 元素的使用者介面。

|UI 元素|描述|
|----------------|-----------------|
|**加入初始設定式**|按一下 [ **加入初始化** ] 方塊，將額外的初始化運算式加入至集合。|
|**相互關聯類型**|指定相互關聯初始設定式的型別。 有四個型別可供選擇：<br /><br /> 1. 用來指定的回呼相互關聯初始化運算式 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 。<br />2. 內容相互關聯初始化運算式來指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 。<br />3. 要求-回復相互關聯初始化運算式來指定 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 。<br />4. 用來指定的查詢相互關聯初始化運算式 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 。<br /><br /> 若要編輯 **CorrelationType**<br /><br /> 1. Tab 至 [ **加入初始化運算式** ] DataGrid 中的特定資料列。<br />2. 按 Ctrl + Tab 將焦點設為 **CorrelationTypeComboBox**<br />3. 按 Alt + 向下 **鍵，以顯示下拉式** 方塊並進行編輯。|
|**XPath 查詢**|索引鍵/值組，其中包含用來從傳入與傳出訊息擷取相互關聯資料的查詢。 使用 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型別時，此清單才有效。|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>若要啟動加入相互關聯初始設定式對話方塊
 [ **加入相互關聯初始化運算式** ] 對話方塊是由 **Send**、 **Receive**、 **receiveandsendreply]** 和 **SendAndReceiveReply** 設計工具所使用。 存取它們在每個案例中都很類似，而牽涉到「 **接收** 設計師」的案例則是用來說明程式。

 [ **Receive** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 [ **Receive** ] 活動設計工具，然後按一下 [加入相互關聯初始化運算式] 對話方塊之 [屬性] 方格中的 [ **CorrelationInitializers** ] 屬性)  (旁邊的省略號按鈕，就會出現 [ **加入相互關聯初始化運算式** ] 對話方塊。

## <a name="see-also"></a>另請參閱
 [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)