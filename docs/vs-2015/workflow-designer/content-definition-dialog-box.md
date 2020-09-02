---
title: 內容定義對話方塊 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656951"
---
# <a name="content-definition-dialog-box"></a>內容定義對話方塊
[**內容定義**] 對話方塊在中用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 來設定、 **Content** 、 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> 和活動的 Content 屬性 <xref:System.ServiceModel.Activities.ReceiveReply> 。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊的活動設計工具，請參閱 [傳送](../workflow-designer/send-activity-designer.md)、 [接收](../workflow-designer/receive-activity-designer.md)、 [receiveandsendreply]](../workflow-designer/receiveandsendreply-template-designer.md)和 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 主題。

 下表說明 [ **初始化相互關聯** ] 對話方塊的使用者介面 (UI) 元素。

|UI 元素|描述|
|----------------|-----------------|
|**訊息**|使用 [訊息 **資料** 運算式] 文字方塊和 [ **訊息類型** ] 下拉式清單方塊的類型，指定訊息內容。 根據預設， **內容定義** 會使用 <xref:System.ServiceModel.Activities.ReceiveMessageContent> ，它需要 <xref:System.ServiceModel.Channels.Message> 工作流程服務定義內的或訊息合約類型。|
|**參數**|按一下要使用的 [ **參數** ] 選項按鈕 <xref:System.ServiceModel.Activities.ReceiveParametersContent> ，這會預期資料合約。 使用資料方格設定 <xref:System.Activities.OutArgument> 索引鍵/值配對的泛型集合，配對的值會指派給目前工作流程中的變數參數。|

 **傳送**、**接收**、 **receiveandsendreply]** 和**SendAndReceiveReply**設計工具會使用 [**內容定義**] 對話方塊。 各種情況的存取方式很類似，在此使用 [Receive] 為例，以說明這個程序。

 [ **Receive** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 [ **Receive** ] 活動設計工具，然後按一下 [內容**定義**] 對話方塊之屬性方格中 [**內容**] (內容) 文字旁的省略號按鈕，就會出現。

 您可以在活動的 [ **訊息** ] 區段內 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 或在活動的 [ **參數** ] 區段中指定內容 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 。

## <a name="see-also"></a>另請參閱
 [Workflow 設計工具 UI 說明](../workflow-designer/workflow-designer-ui-help.md)