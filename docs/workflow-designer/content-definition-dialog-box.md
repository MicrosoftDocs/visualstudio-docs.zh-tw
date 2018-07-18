---
title: 工作流程設計工具-內容定義對話方塊
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc434e35755b04054d1e24da97e8a4699af7df0e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757947"
---
# <a name="content-definition-dialog-box"></a>內容定義對話方塊

**內容定義** 對話方塊中設定時，會在工作流程設計工具**內容**的屬性<xref:System.ServiceModel.Activities.Send>， <xref:System.ServiceModel.Activities.Receive>， <xref:System.ServiceModel.Activities.SendReply>，以及<xref:System.ServiceModel.Activities.ReceiveReply>活動。 如需有關使用這個方塊的活動設計工具的詳細資訊，請參閱 <<c0> [ 傳送](../workflow-designer/send-activity-designer.md)，[接收](../workflow-designer/receive-activity-designer.md)， [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)，和[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)主題。

下表描述的使用者介面 (UI) 項目**初始化相互關聯** 對話方塊中：

|UI 項目|描述|
|----------------|-----------------|
|**訊息**|指定的訊息內容，其中**訊息資料**運算式文字方塊中，使用的型別**訊息類型**下拉式清單方塊。 根據預設，**內容定義**會使用<xref:System.ServiceModel.Activities.ReceiveMessageContent>，這會預期<xref:System.ServiceModel.Channels.Message>或訊息合約中的工作流程服務定義的型別。|
|**參數**|按一下 **參數**選項按鈕，以使用<xref:System.ServiceModel.Activities.ReceiveParametersContent>，這會預期的資料合約。 使用資料方格設定 <xref:System.Activities.OutArgument> 索引鍵/值配對的泛型集合，配對的值會指派給目前工作流程中的變數參數。|

**內容定義** 對話方塊由**傳送**，**接收**， **ReceiveAndSendReply**，和**SendAndReceiveReply**設計工具。 各種情況的存取方式很類似，在此使用 [Receive] 為例，以說明這個程序。

**接收**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論通常用來放置活動。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，具有 Receive 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 選取 **接收**活動設計工具 和 （內容） 文字旁邊的省略符號按鈕的 click**內容**屬性的屬性方格中**內容定義**才會出現的對話方塊。

可以在指定的內容**訊息**一節<xref:System.ServiceModel.Activities.ReceiveMessageContent>活動或內**參數**區段<xref:System.ServiceModel.Activities.ReceiveParametersContent>活動。

## <a name="see-also"></a>另請參閱

- [工作流程設計工具 UI 說明](../workflow-designer/workflow-designer-ui-help.md)