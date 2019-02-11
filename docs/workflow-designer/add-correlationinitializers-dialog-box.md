---
title: 工作流程設計工具-CorrelationInitializers [新增] 對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82bc9908535fe555030f3e9e4d6699dc6d0b6509
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938783"
---
# <a name="add-correlationinitializers-dialog-box"></a>加入相互關聯初始設定式對話方塊

**加入相互關聯初始設定式** 對話方塊中設定時，會在工作流程設計工具**CorrelationInitializers**的屬性<xref:System.ServiceModel.Activities.Send>， <xref:System.ServiceModel.Activities.Receive>， <xref:System.ServiceModel.Activities.SendReply>，及<xref:System.ServiceModel.Activities.ReceiveReply>活動。 如需有關使用這個方塊的活動設計工具的詳細資訊，請參閱 <<c0> [ 傳送](../workflow-designer/send-activity-designer.md)，[接收](../workflow-designer/receive-activity-designer.md)， [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)，和[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)主題。

使用此對話方塊中指定的集合中的相互關聯初始設定式可以初始化傳訊活動之間的下列關聯性：

- 以查詢為基礎
- 內容
- 回呼內容
- request-reply

下表描述的使用者介面 (UI) 項目**加入相互關聯初始設定式** 對話方塊中：

|UI 項目|描述|
|-|-----------------|
|**新增初始設定式**|按一下 **新增初始化**方塊將額外的初始設定式新增至集合。|
|**相互關聯類型**|指定相互關聯初始設定式的型別。 有四個型別可供選擇：<br /><br /> 1.指定 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 的回呼相互關聯初始設定式。<br />2.指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 的內容相互關聯初始設定式。<br />3.指定 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> 的要求-回覆相互關聯初始設定式。<br />4.指定 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 的查詢相互關聯初始設定式。<br /><br /> 若要編輯**相互關聯類型**<br /><br /> 1.中的特定資料列的索引標籤**新增初始設定式**DataGrid。<br />2.若要將焦點設定為**CorrelationTypeComboBox**，按下**Ctrl**+**索引標籤**。<br />3.按下 Alt + 向下鍵來快顯**ComboBox**並加以編輯。|
|**XPath 查詢**|索引鍵/值組，其中包含用來從傳入與傳出訊息擷取相互關聯資料的查詢。 使用 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型別時，此清單才有效。|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>若要啟動加入相互關聯初始設定式對話方塊

 **加入相互關聯初始設定式** 對話方塊由**傳送**，**接收**， **ReceiveAndSendReply**，和**SendAndReceiveReply**設計工具。 存取方式很類似，在每一個案例中，而且牽涉到的情況**接收**設計工具此處用來說明這個程序。

 **接收**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論用來放置活動。 卸除**接收**活動設計工具會建立<xref:System.ServiceModel.Activities.Receive>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的接收。 選取 **接收**活動設計工具 和 （集合） 文字旁邊的省略符號按鈕的 click **CorrelationInitializers**屬性的屬性方格中**新增相互關聯初始設定式**出現的對話方塊。

## <a name="see-also"></a>另請參閱

- [加入相互關聯對話方塊](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)