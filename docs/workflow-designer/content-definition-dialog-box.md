---
title: 工作流程設計工具-內容定義對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19e2341d458c98f01d3b58d6f77887ac1cfe6746
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876199"
---
# <a name="content-definition-dialog-box"></a>內容定義對話方塊

[**內容定義**] 對話方塊會在工作流程設計工具中用來設定**Content** <xref:System.ServiceModel.Activities.Send> 、 <xref:System.ServiceModel.Activities.Receive> 、 <xref:System.ServiceModel.Activities.SendReply> 和活動的內容屬性 <xref:System.ServiceModel.Activities.ReceiveReply> 。 如需使用此方塊之活動設計工具的詳細資訊，請參閱[Send](../workflow-designer/send-activity-designer.md)、 [Receive](../workflow-designer/receive-activity-designer.md)、 [receiveandsendreply]](../workflow-designer/receiveandsendreply-template-designer.md)和[sendandreceivereply]](../workflow-designer/sendandreceivereply-template-designer.md)主題。

下表描述 [**初始化相互關聯**] 對話方塊的使用者介面（UI）元素：

|UI 元素|描述|
|-|-----------------|
|**訊息**|使用 [訊息**資料**運算式] 文字方塊和 [**訊息類型**] 下拉式清單方塊來指定訊息內容。 根據預設，**內容定義**會使用 <xref:System.ServiceModel.Activities.ReceiveMessageContent> ，其需要 <xref:System.ServiceModel.Channels.Message> 工作流程服務定義內的或訊息合約類型。|
|**參數**|按一下 [**參數**] 選項按鈕以使用 <xref:System.ServiceModel.Activities.ReceiveParametersContent> ，其預期會有資料合約。 使用資料方格設定 <xref:System.Activities.OutArgument> 索引鍵/值配對的泛型集合，配對的值會指派給目前工作流程中的變數參數。|

[**內容定義**] 對話方塊是由**傳送**、**接收**、 **receiveandsendreply]** 和**sendandreceivereply]** 設計工具所使用。 各種情況的存取方式很類似，在此使用 [Receive] 為例，以說明這個程序。

[ **Receive** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 [ **Receive** ] 活動設計工具，然後按一下屬性方格中 [**內容**] 屬性的 [（內容）] 文字旁邊的省略號按鈕，以顯示 [**內容定義**] 對話方塊。

內容可以在活動的**訊息**區段中指定， <xref:System.ServiceModel.Activities.ReceiveMessageContent> 或是在活動的**參數**區段內指定 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 。

## <a name="see-also"></a>另請參閱

- [Workflow 設計工具 UI 說明](browse-and-select-a-dotnet-type-dialog-box.md)