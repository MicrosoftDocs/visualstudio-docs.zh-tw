---
title: 工作流程設計工具-新增 CorrelationInitializers 對話方塊
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
ms.openlocfilehash: 9d2a0b0f7c76b392d5d2d0135c3ab6e370f8678e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114293"
---
# <a name="add-correlationinitializers-dialog-box"></a>加入相互關聯初始設定式對話方塊

[**新增相互關聯初始化運算式**] 對話方塊用於工作流程設計工具中，以設定 <xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的**CorrelationInitializers**屬性。 如需使用此方塊之活動設計工具的詳細資訊，請參閱[Send](../workflow-designer/send-activity-designer.md)、 [Receive](../workflow-designer/receive-activity-designer.md)、 [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md)和[sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md)主題。

使用此對話方塊所指定之集合中的相互關聯初始化運算式，可以初始化訊息活動之間的下列相互關聯：

- 以查詢為基礎
- 內容
- 回呼內容
- 要求-回復

下表描述 [**新增相互關聯初始化運算式**] 對話方塊的使用者介面（UI）元素：

|UI 項目|描述|
|-|-----------------|
|**新增初始化運算式**|按一下 [**加入初始化**] 方塊，將其他初始化運算式加入至集合。|
|**相互關聯類型**|指定相互關聯初始設定式的型別。 有四個型別可供選擇：<br /><br /> 1. 回呼相互關聯初始化運算式，用來指定 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>。<br />2. 內容相互關聯初始化運算式，用來指定 <xref:System.ServiceModel.Activities.CorrelationInitializer>。<br />3. 要求-回復相互關聯初始化運算式以指定 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>。<br />4. 查詢相互關聯初始化運算式，用來指定 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>。<br /><br /> 若要編輯**CorrelationType**<br /><br /> 1. Tab 至**Add 初始化運算式**DataGrid 中的特定資料列。<br />2. 若要將焦點設定為**CorrelationTypeComboBox**，請按**Ctrl**+索引標籤。<br />3. 按 Alt + 向下鍵可顯示**ComboBox**並加以編輯。|
|**XPath 查詢**|索引鍵/值組，其中包含用來從傳入與傳出訊息擷取相互關聯資料的查詢。 使用 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 型別時，此清單才有效。|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>若要啟動加入相互關聯初始設定式對話方塊

 **新增相互關聯初始化運算式** 對話方塊是由**傳送**、**接收**、 **receiveandsendreply**和**sendandreceivereply**設計工具所使用。 存取它們在每個案例中都很類似，而涉及**接收**設計工具的案例則是用來說明此程式。

 [ **Receive** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上放置活動的地方。 卸載 [ **receive** ] 活動設計工具會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，其中包含預設的 Receive <xref:System.Activities.Activity.DisplayName%2A>。 選取 [ **Receive** ] 活動設計工具，然後按一下屬性方格中 [ **CorrelationInitializers** ] 屬性的（集合）文字旁邊的省略號按鈕，就會出現 [**加入相互關聯初始化運算式**] 對話方塊。

## <a name="see-also"></a>請參閱

- [初始化相互關聯對話方塊](../workflow-designer/initialize-correlation-dialog-box.md)
