---
title: Sendandreceivereply 範本設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663275"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 樣本設計工具
**Sendandreceivereply**範本是用來建立一對預先設定的 <xref:System.ServiceModel.Activities.Send>，並 <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.Activities.Statements.Sequence> 活動內的活動，這些活動會在用戶端上以要求/回應訊息交換模式的一部分相互關聯。

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 範本
 除了在 <xref:System.Activities.Statements.Sequence> 活動內建立 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動之外，新增**sendandreceivereply**範本還會執行三件事：

1. 設定 <xref:System.ServiceModel.Activities.Send.OperationName%2A> 活動的 <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> 與 <xref:System.ServiceModel.Activities.Send> 屬性。

2. 將 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

3. 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="using-the-sendandreceivereply-template-designer"></a>使用 SendAndReceiveReply 範本設計工具
 [ **Sendandreceivereply]** ] 活動設計**工具**位於 [工具箱] 的 [**訊息**] 類別中，若要存取，請按一下 [[!INCLUDE[wfd2](../includes/wfd2-md.md)] 上的 [**工具箱**] 索引標籤（也可以從**視圖**選取 [**工具列**]）。功能表，或按 CTRL + ALT + X）。

 **Sendandreceivereply** ] 活動設計工具可以從 [**工具箱** 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動的任一處。 這會建立可使用 [**傳送**] 活動設計工具設定的 <xref:System.ServiceModel.Activities.Send> 活動，以及可以使用 [ **ReceiveReplyForSend** ] 設計工具設定的相互關聯 <xref:System.ServiceModel.Activities.ReceiveReply>。

 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用**傳送**設計工具來設定 <xref:System.ServiceModel.Activities.Send> 活動，請參閱[傳送](../workflow-designer/send-activity-designer.md)主題。

 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用**ReceiveReplyForSend**設計工具來設定 <xref:System.ServiceModel.Activities.ReceiveReply> 活動，請參閱下一節。

### <a name="properties-of-receivereply"></a>ReceiveReply 的屬性
 下表顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|                                 屬性名稱                                 | 必要 |                                                                                                                                                                                                                                                                                                                                                        使用量                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  偽   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.ReceiveReply> 活動可選用的易記名稱。 預設為 ReceiveReplyForSend。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | 參考到與這個 <xref:System.ServiceModel.Activities.Send> 活動成對的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 這個屬性不得為**null**。 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動會在用戶端上一起使用，以建立要求/回應訊息模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.Send> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  偽   |                        指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 按一下屬性方格中 [**內容**] 欄位旁邊的省略號按鈕，或按一下 [**定義 ...** ]，即可編輯此屬性。 [ **Receive** ] 活動設計工具介面上 [**內容**] 標籤旁的按鈕。 兩者都會顯示 [**內容定義**] 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)] 如何使用此方塊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  偽   |              指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下 [屬性] 方格中 [<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>] 屬性旁的省略號按鈕，以開啟 [**加入相互關聯初始化運算式**] 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊，請參閱[新增 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  偽   |                                                                                                                                                                                                                                               指定訊息的動作標頭。 如果沒有明確設定，其值會預設為：<br /><br /> <strong>https://tempuri.org/{service 合約命名空間}/合約名稱}/{作業名稱}。</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>另請參閱
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [接收](../workflow-designer/receive-activity-designer.md) [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md) [傳送](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)