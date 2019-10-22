---
title: 工作流程設計工具 InitializeCorrelation 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650217"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 活動設計工具

[ **InitializeCorrelation** ] 活動設計工具會用來建立和設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動。 @No__t_0 活動會在傳送或接收訊息之前先建立相互關聯。

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 活動

<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動會用來在不傳送或接收訊息的情況下初始化相互關聯。 相互關聯通常會在傳送或接收訊息時初始化。 如果必須在傳送或接收訊息之前建立相互關聯，請使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 來初始化相互關聯。

### <a name="using-the-initializecorrelation-activity-designer"></a>使用 InitializeCorrelation 活動設計工具

在 [工具箱] 的 [**訊息**] 分類中，存取 [ **InitializeCorrelation** ] 活動設計**工具**。

[ **InitializeCorrelation** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上。 卸載活動設計工具會建立具有預設 <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation 的 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動。 @No__t_0 可以在 [ **InitializeCorrelation** ] 活動設計工具的標頭中編輯，或是在 [**屬性**] 視窗的 [ **DisplayName** ] 方塊中編輯。

@No__t_0 可以在 [ **InitializeCorrelation** ] 活動設計工具介面上的 [**屬性**] 視窗的 [相互**關聯**] 欄位中指定。

若要顯示 [**初始化相互關聯**] 對話方塊，您可以在其中指定相互關聯控制碼和用來初始化它的索引鍵/值組，請選取 [**屬性**] 視窗中 [ **CorrelationData** ] 欄位旁的省略號按鈕。 或者，選取 [View ...]**InitializeCorrelation**活動設計工具介面上的提示文字。 如需使用此對話方塊的詳細資訊，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)一文。

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 屬性

下表顯示 <xref:System.ServiceModel.Activities.InitializeCorrelation> 屬性，並描述它們在設計工具中的使用方式。 這些屬性可以在 [**屬性**] 視窗中或在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動的易記名稱。 預設值為 InitializeCorrelation。<br /><br /> 雖然不一定要使用易記 <xref:System.Activities.Activity.DisplayName%2A> 的非預設值，但建議您這麼做。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|用於與相互關聯中工作流程活動相關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|相互關聯資料的字典，該字典會使訊息與工作流程執行個體產生關聯。<br /><br /> 使用 [**初始化相互關聯**] 對話方塊來設定 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>。 如需使用此對話方塊的詳細資訊，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)一文。|

## <a name="see-also"></a>請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)