---
title: 工作流程設計工具-ReceiveAndSendReply 範本設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 525b7deb0b40ee6952c803c9c98b212c6ed0d224
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979330"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 樣板設計工具

**ReceiveAndSendReply**範本用來建立一對預先設定<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>內的活動<xref:System.Activities.Statements.Sequence>做為要求/回應訊息交換的一部分相互關聯的活動在伺服器上的模式。

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 範本

加入**ReceiveAndSendReply**範本一樣三件事，除了建立<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動<xref:System.Activities.Statements.Sequence>活動：

1.  設定 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 活動的 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 與 <xref:System.ServiceModel.Activities.Receive> 屬性。

2.  將 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.Receive> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

3.  建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="using-the-receiveandsendreply-template-designer"></a>使用 ReceiveAndSendReply 範本設計工具
 **ReceiveAndSendReply**活動設計工具位於**傳訊**分類**工具箱**，即可存取的哪一個**工具箱**中工作流程設計工具 索引標籤 (或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **ReceiveAndSendReply**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面上的任何活動通常放置的位置。 這會建立<xref:System.ServiceModel.Activities.Receive>活動，您可以使用設定**傳送**活動設計工具以及相互關聯<xref:System.ServiceModel.Activities.SendReply>，可以設定與 SendReplyToReceive 設計工具。

 如需有關使用**接收**設計工具設定<xref:System.ServiceModel.Activities.Receive>活動，請參閱[接收](../workflow-designer/receive-activity-designer.md)主題。

 如需有關使用**SendReplyToReceive**設計工具設定<xref:System.ServiceModel.Activities.SendReply>活動，請參閱下一節。

### <a name="properties-of-sendreply"></a>SendReply 的屬性
 下表顯示 <xref:System.ServiceModel.Activities.SendReply> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中編輯，有些可以在工作流程設計工具的設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.SendReply> 活動可選用的易記名稱。 預設為 SendReplyToReceive。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|參考到與這個 <xref:System.ServiceModel.Activities.Receive> 活動成對的 <xref:System.ServiceModel.Activities.SendReply> 活動。 這個屬性不能**null**。 伺服器會同時使用 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動，以製作要求/回應傳訊模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計工具中，您不能編輯這個屬性，因為這個屬性自動繫結至您先前建立 <xref:System.ServiceModel.Activities.Send> 活動的來源 <xref:System.ServiceModel.Activities.SendReply> 活動。|
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 編輯這個屬性旁邊的橢圓形按鈕，即可**內容**在屬性方格，或按一下欄位**定義...** 按鈕**內容**上加上標籤**接收**活動設計工具介面。 兩者都顯示**內容定義**對話方塊。 如需如何使用此方塊的詳細資訊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)主題。|
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下省略符號按鈕旁的 [<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>屬性以開啟 [屬性] 方格中的**加入相互關聯初始設定式**] 對話方塊。 如需使用此方塊的詳細資訊，請參閱[加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)主題。|
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|指定訊息的動作標頭。 如果沒有明確設定，其值會預設為：<br /><br /> **https://tempuri.org/{service 合約命名空間} / {服務合約名稱} / {作業名稱}**|
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|指定傳送回覆訊息前是否要保存工作流程執行個體。 預設值為 **false**。|

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [接收](../workflow-designer/receive-activity-designer.md)
- [傳送](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)