---
title: "InitializeCorrelation 活動設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f6f39f25e7a4cf589b43fcf3b3f84b9784241961
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 活動設計工具
**InitializeCorrelation**活動設計工具用來建立及設定<xref:System.ServiceModel.Activities.InitializeCorrelation>用來建立訊息之前傳送或接收它們之間的相互關聯的活動。

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 活動
 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動會用來在不傳送或接收訊息的情況下初始化相互關聯。 相互關聯通常會在傳送或接收訊息時初始化。 如果必須在傳送或接收訊息之前建立相互關聯，請使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 來初始化相互關聯。

### <a name="using-the-initializecorrelation-activity-designer"></a>使用 InitializeCorrelation 活動設計工具
 **InitializeCorrelation**活動設計工具位於**傳訊**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **InitializeCorrelation**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面。 這會建立<xref:System.ServiceModel.Activities.InitializeCorrelation>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的 InitializeCorrelation.The<xref:System.Activities.Activity.DisplayName%2A>可編輯的標頭中**InitializeCorrelation**活動設計工具或在**DisplayName**方塊**屬性**視窗。

 <xref:System.ServiceModel.Activities.CorrelationHandle>可以是指定在**相互關聯**欄位**屬性**視窗上的**InitializeCorrelation**活動設計工具介面。

 按一下省略符號按鈕，除了**CorrelationData**欄位**屬性**視窗或 檢視 提示文字上的**InitializeCorrelation**活動設計工具介面會顯示**初始化相互關聯** 對話方塊可指定相互關聯控制代碼，用來初始化它的索引鍵-值組。 如需使用此對話方塊的詳細資訊，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)主題。

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 屬性
 下表顯示 <xref:System.ServiceModel.Activities.InitializeCorrelation> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在編輯**屬性**視窗或在[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動的易記名稱。 預設值為 InitializeCorrelation。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|用於與相互關聯中工作流程活動相關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|相互關聯資料的字典，該字典會使訊息與工作流程執行個體產生關聯。<br /><br /> 使用**初始化相互關聯**對話方塊來設定<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>。 如需有關使用此對話方塊，請參閱[型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md)主題。|

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [傳送](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)