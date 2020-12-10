---
title: InitializeCorrelation 活動設計工具
description: 在工作流程設計工具中，您可以瞭解如何使用 InitializeCorrelation 活動設計工具來建立和設定 InitializeCorrelation 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ef70cb452c01917f65619d400c21ed18ed11721
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993194"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 活動設計工具

**InitializeCorrelation** 活動設計工具是用來建立及設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動。 <xref:System.ServiceModel.Activities.InitializeCorrelation>活動會先在訊息之間建立相互關聯，然後再傳送或接收訊息。

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 活動

<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動會用來在不傳送或接收訊息的情況下初始化相互關聯。 相互關聯通常會在傳送或接收訊息時初始化。 如果必須在傳送或接收訊息之前建立相互關聯，請使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 來初始化相互關聯。

### <a name="using-the-initializecorrelation-activity-designer"></a>使用 InitializeCorrelation 活動設計工具

存取 [工具箱] 的 [**訊息**] 類別中的 [ **InitializeCorrelation** ] 活動設計 **工具**。

[ **InitializeCorrelation** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上。 卸載活動設計工具會建立 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動，預設值是 <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **InitializeCorrelation** ] 活動設計工具的標頭中編輯，或是在 [**屬性**] 視窗的 [ **DisplayName** ] 方塊中編輯。

<xref:System.ServiceModel.Activities.CorrelationHandle>可以在 [ **InitializeCorrelation** ] 活動設計工具介面上的 [**屬性**] 視窗的 [相互 **關聯**] 欄位中指定。

若要顯示 [**初始化相互關聯**] 對話方塊，您可以在其中指定相互關聯控制碼以及用來初始化它的索引鍵/值組，請選取 [**屬性**] 視窗中 [ **CorrelationData** ] 欄位旁的省略號按鈕。 或者，選取 [View ...] **InitializeCorrelation** 活動設計工具介面上的提示文字。 如需使用這個對話方塊的詳細資訊，請參閱 [型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md) 一文。

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 屬性

下表顯示這些 <xref:System.ServiceModel.Activities.InitializeCorrelation> 屬性，並描述它們在設計工具中的使用方式。 這些屬性可以在 [ **屬性** ] 視窗中或在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動的易記名稱。 預設值為 InitializeCorrelation。<br /><br /> 雖然不是絕對需要針對易記使用非預設值 <xref:System.Activities.Activity.DisplayName%2A> ，但建議使用。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|否|用於與相互關聯中工作流程活動相關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|否|相互關聯資料的字典，該字典會使訊息與工作流程執行個體產生關聯。<br /><br /> 使用 [ **初始化相互關聯** ] 對話方塊來設定 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 。 如需使用這個對話方塊的詳細資訊，請參閱 [型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md) 一文。|

## <a name="see-also"></a>另請參閱

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [收到](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)