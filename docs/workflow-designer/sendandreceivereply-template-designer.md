---
title: 工作流程設計工具-SendAndReceiveReply 範本設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22cdd114a11ff9d1b3b162009cc77d83aec1fd83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858962"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 樣本設計工具

**SendAndReceiveReply**範本用來建立一對預先設定<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.ReceiveReply>活動。 活動屬於<xref:System.Activities.Statements.Sequence>活動，並相互關聯的用戶端上的要求/回應訊息交換模式一部分。

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 範本

新增**SendAndReceiveReply**範本會執行三件事，除了建立<xref:System.ServiceModel.Activities.Send>並<xref:System.ServiceModel.Activities.ReceiveReply>內的活動<xref:System.Activities.Statements.Sequence>活動：

- 會設定<xref:System.ServiceModel.Activities.Send.OperationName%2A>並<xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>屬性的<xref:System.ServiceModel.Activities.Send>活動。

- 將 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 活動的 <xref:System.ServiceModel.Activities.ReceiveReply> 屬性繫結至 <xref:System.ServiceModel.Activities.Send> 活動。

- 建立 <xref:System.ServiceModel.Activities.CorrelationHandle>，做為父系活動的一個變數。

### <a name="use-the-sendandreceivereply-template-designer"></a>使用 SendAndReceiveReply 範本設計工具

存取權**SendAndReceiveReply**中的活動設計工具**Messaging**類別**工具箱**。 **SendAndReceiveReply**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論通常用來放置活動。 卸除活動設計工具會建立<xref:System.ServiceModel.Activities.Send>可以使用設定的活動**傳送**活動設計工具] 和 [相互關聯<xref:System.ServiceModel.Activities.ReceiveReply>可以使用設定**ReceiveReplyForSend**設計工具。

如需使用詳細資訊**傳送**設計工具設定<xref:System.ServiceModel.Activities.Send>活動，請參閱[傳送](../workflow-designer/send-activity-designer.md)。

### <a name="properties-of-receivereply"></a>ReceiveReply 的屬性

下表顯示<xref:System.ServiceModel.Activities.ReceiveReply>屬性，並說明它們在設計工具的使用方式。 這些屬性可以在 [屬性] 方格中編輯，有些可以在工作流程設計工具介面上編輯。


| 屬性名稱 | 必要項 | 使用方式 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.ReceiveReply> 活動可選用的易記名稱。 預設為 ReceiveReplyForSend。<br /><br /> 雖然使用非預設值，做為易記<xref:System.Activities.Activity.DisplayName%2A>不是絕對必要，建議您最好使用這類的值。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | 參考到與這個 <xref:System.ServiceModel.Activities.Send> 活動成對的 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。 這個屬性不能**null**。 用戶端會同時使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動，以製作要求/回應傳訊模式的模型。 這個屬性會指定哪個 <xref:System.ServiceModel.Activities.Send> 活動為成對的活動。 在設計師中，您無法編輯屬性，因為自動繫結至<xref:System.ServiceModel.Activities.Send>活動在您建立的<xref:System.ServiceModel.Activities.ReceiveReply>活動。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | 指定要接收的訊息或參數內容。 這可以是 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 活動或 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 活動。 編輯這個屬性，依序按一下省略符號按鈕旁**內容**在屬性方格中，或按一下欄位**定義**按鈕旁邊**內容**上加上標籤**接收**活動設計工具介面。 兩者都顯示**內容定義**對話方塊。 如需如何使用這個方塊的詳細資訊，請參閱[內容定義對話方塊](../workflow-designer/content-definition-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | 指定 <xref:System.ServiceModel.Activities.CorrelationInitializer> 物件的集合，這些物件會初始化多個 <xref:System.ServiceModel.Activities.CorrelationHandle> 物件，用來設定工作流程內的這個 <xref:System.ServiceModel.Activities.Receive> 活動。 按一下省略符號按鈕旁<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>以開啟 屬性 方格中的屬性**加入相互關聯初始設定式** 對話方塊。 如需使用此方塊的詳細資訊，請參閱[加入 CorrelationInitializers 對話方塊](../workflow-designer/add-correlationinitializers-dialog-box.md)。 |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | 指定訊息的動作標頭。 如果未明確設定，其值會預設為：<br /><br /> <strong>https://tempuri.org/{service 合約命名空間} / {服務合約名稱} / {作業名稱}。</strong> |

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)