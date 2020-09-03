---
title: Receiveandsendreply] 範本設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395382"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 樣板設計工具
**Receiveandsendreply]** 範本是用來在活動內建立一對預先設定的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.SendReply> 活動 <xref:System.Activities.Statements.Sequence> ，這些活動會在伺服器上相互關聯為要求/回應訊息交換模式的一部分。

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 範本
 新增 **receiveandsendreply]** 範本除了 <xref:System.ServiceModel.Activities.Receive> 使用活動建立和活動之外，還會執行三件事 <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.Statements.Sequence> ：

1. 設定 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 活動的 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 與 <xref:System.ServiceModel.Activities.Receive> 屬性。

2. 將 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.Receive> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

3. 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="using-the-receiveandsendreply-template-designer"></a>使用 ReceiveAndSendReply 範本設計工具
 [ **Receiveandsendreply]** ] 活動設計工具位於 [**工具箱**] 的 [**訊息**] 類別中，若要存取，請按一下 (中的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 也可以從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **Receiveandsendreply]** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。 這會建立一個 <xref:System.ServiceModel.Activities.Receive> 活動，您可以使用 [ **傳送** ] 活動設計工具和 <xref:System.ServiceModel.Activities.SendReply> 可使用 SendReplyToReceive 設計工具設定的相互關聯來設定活動。

 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用 **接收** 設計工具來設定 <xref:System.ServiceModel.Activities.Receive> 活動，請參閱「 [接收](../workflow-designer/receive-activity-designer.md) 」主題。

 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用 **SendReplyToReceive** 設計工具來設定 <xref:System.ServiceModel.Activities.SendReply> 活動，請參閱下一節。

### <a name="properties-of-sendreply"></a>SendReply 的屬性
 下表顯示 <xref:System.ServiceModel.Activities.SendReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。

|                               屬性名稱                                | 必要 |                                                                                                                                                                                                                                                                                                                                                      使用方式                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  否   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.SendReply> 活動可選用的易記名稱。 預設為 SendReplyToReceive。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   是   | 參考到與這個 <xref:System.ServiceModel.Activities.Receive> 活動成對的 <xref:System.ServiceModel.Activities.SendReply> 活動。 這個屬性不得為 **null**。 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動會一起用於伺服器上，以建立要求/回應訊息模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.Send> 活動的 <xref:System.ServiceModel.Activities.SendReply> 活動。 |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  否   |                       指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 若要編輯這個屬性，請按一下屬性方格中 [**內容**] 欄位旁邊的省略號按鈕，或按一下 [**定義 ...** ]。 按鈕（位於 [ **Receive** ] 活動設計工具介面上的 [**內容**] 標籤旁邊）。 兩者都會顯示 [ **內容定義** ] 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)] 如何使用此方塊，請參閱 [內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md) 主題。                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  否   |            指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下屬性方格中屬性旁邊的省略號按鈕， <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 以開啟 [加入相互 **關聯初始化運算式** ] 對話方塊。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用此方塊，請參閱 [加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md) 主題。            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  否   |                                                                                                                                                                                                                                              指定訊息的動作標頭。 如果沒有明確設定，其值會預設為：<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  否   |                                                                                                                                                                                                                                                                                          指定傳送回覆訊息前是否要保存工作流程執行個體。 預設值為 **false**。                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>另請參閱
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [接收](../workflow-designer/receive-activity-designer.md)[傳送](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)