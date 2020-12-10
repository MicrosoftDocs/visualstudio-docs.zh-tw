---
title: '[新增 CorrelationInitializers] 對話方塊'
description: 瞭解如何使用工作流程設計工具中的 [加入相互關聯初始化運算式] 對話方塊，設定傳送、接收和 SendReply 活動的 CorrelationInitializers 屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e5822d1dc79835dd6fdcc3a70c3392dbd3d1aab
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996353"
---
# <a name="add-correlationinitializers-dialog-box"></a>加入相互關聯初始設定式對話方塊

[**加入相互關聯初始化運算式**] 對話方塊會在工作流程設計工具中用來設定、、 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> 和活動的 CorrelationInitializers 屬性 <xref:System.ServiceModel.Activities.ReceiveReply> 。 如需使用此方塊之活動設計工具的詳細資訊，請參閱 [傳送](../workflow-designer/send-activity-designer.md)、 [接收](../workflow-designer/receive-activity-designer.md)、 [receiveandsendreply]](../workflow-designer/receiveandsendreply-template-designer.md)和 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 主題。

使用此對話方塊指定之集合中的相互關聯初始化運算式，可以初始化訊息活動之間的下列相互關聯：

- 以查詢為基礎
- 內容
- 回呼內容
- 要求-回復

下表描述 [ **加入相互關聯初始化運算式** ] 對話方塊的使用者介面 (UI) 元素：

|UI 元素|描述|
|-|-----------------|
|**加入初始設定式**|按一下 [ **加入初始化** ] 方塊，將額外的初始化運算式加入至集合。|
|**相互關聯類型**|指定相互關聯初始設定式的型別。 有四個型別可供選擇：<br /><br /> 1. 用來指定的回呼相互關聯初始化運算式 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 。<br />2. 內容相互關聯初始化運算式來指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 。<br />3. 要求-回復相互關聯初始化運算式來指定 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 。<br />4. 用來指定的查詢相互關聯初始化運算式 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 。<br /><br /> 若要編輯 **CorrelationType**<br /><br /> 1. Tab 至 [ **加入初始化運算式** ] DataGrid 中的特定資料列。<br />2. 若要將焦點設定為 **CorrelationTypeComboBox**，請按下 **Ctrl** + **tab**。<br />3. 按 Alt + 向下 **鍵，以顯示下拉式** 方塊並進行編輯。|
|**XPath 查詢**|索引鍵/值組，其中包含用來從傳入與傳出訊息擷取相互關聯資料的查詢。 使用 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型別時，此清單才有效。|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>若要啟動加入相互關聯初始設定式對話方塊

 [ **加入相互關聯初始化運算式** ] 對話方塊是由 **Send**、 **Receive**、 **receiveandsendreply]** 和 **SendAndReceiveReply** 設計工具所使用。 存取它們在每個案例中都很類似，在這裡使用「 **接收** 設計工具」的案例來說明程式。

 [ **Receive** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上放置活動的任一處。 卸載 [ **receive** ] 活動設計工具會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> Receive。 選取 [ **Receive** ] 活動設計工具，然後按一下 [加入相互關聯初始化運算式] 對話方塊之 [屬性] 方格中的 [ **CorrelationInitializers** ] 屬性)  (旁邊的省略號按鈕，就會出現 [ **加入相互關聯初始化運算式** ] 對話方塊。

## <a name="see-also"></a>另請參閱

- [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)
