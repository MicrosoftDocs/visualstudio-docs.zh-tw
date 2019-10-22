---
title: '[內容定義] 對話方塊 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656951"
---
# <a name="content-definition-dialog-box"></a>內容定義對話方塊
[**內容定義**] 對話方塊用於 [!INCLUDE[wfd1](../includes/wfd1-md.md)]，以設定 <xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的**內容**屬性。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊的活動設計工具，請參閱[Send](../workflow-designer/send-activity-designer.md)、 [Receive](../workflow-designer/receive-activity-designer.md)、 [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md)和[sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md)主題。

 下表描述 [**初始化相互關聯**] 對話方塊的使用者介面（UI）元素。

|UI 項目|描述|
|----------------|-----------------|
|**訊息**|使用 [訊息**資料**運算式] 文字方塊和 [**訊息類型**] 下拉式清單方塊來指定訊息內容。 根據預設，**內容定義**會使用 <xref:System.ServiceModel.Activities.ReceiveMessageContent>，這需要工作流程服務定義內的 <xref:System.ServiceModel.Channels.Message> 或訊息合約類型。|
|**參數**|按一下 [**參數**] 選項按鈕，以使用需要資料合約的 <xref:System.ServiceModel.Activities.ReceiveParametersContent>。 使用資料方格設定 <xref:System.Activities.OutArgument> 索引鍵/值配對的泛型集合，配對的值會指派給目前工作流程中的變數參數。|

 **內容定義** 對話方塊是由**傳送**、**接收**、 **receiveandsendreply**和**sendandreceivereply**設計工具所使用。 各種情況的存取方式很類似，在此使用 [Receive] 為例，以說明這個程序。

 [ **Receive** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 [ **Receive** ] 活動設計工具，然後按一下屬性方格中 [**內容**] 屬性的 [（內容）] 文字旁邊的省略號按鈕，以顯示 [**內容定義**] 對話方塊。

 您可以在 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動的**訊息**區段中，或在 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動的**參數**區段中指定內容。

## <a name="see-also"></a>請參閱
 [工作流程設計工具 UI 說明](../workflow-designer/workflow-designer-ui-help.md)