---
title: InitializeCorrelation 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659027"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 活動設計工具
[ **InitializeCorrelation** ] 活動設計工具會用來建立及設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動，此活動會在傳送或接收訊息之前，用來建立訊息之間的相互關聯。

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 活動
 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動會用來在不傳送或接收訊息的情況下初始化相互關聯。 相互關聯通常會在傳送或接收訊息時初始化。 如果必須在傳送或接收訊息之前建立相互關聯，請使用 <xref:System.ServiceModel.Activities.InitializeCorrelation> 來初始化相互關聯。

### <a name="using-the-initializecorrelation-activity-designer"></a>使用 InitializeCorrelation 活動設計工具
 [ **InitializeCorrelation** ] 活動設計工具位於 [**工具箱**] 的 [**訊息**] 類別中，若要存取，請按一下 (上的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **InitializeCorrelation** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上。 這會建立一個 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動，其預設值 <xref:System.Activities.Activity.DisplayName%2A> 為 InitializeCorrelation <xref:System.Activities.Activity.DisplayName%2A> 。可以在 [ **InitializeCorrelation** ] 活動設計工具的標頭中編輯，或是在 [**屬性**] 視窗的 [ **DisplayName** ] 方塊中編輯。

 <xref:System.ServiceModel.Activities.CorrelationHandle>可以在 [ **InitializeCorrelation** ] 活動設計工具介面上的 [**屬性**] 視窗的 [相互**關聯**] 欄位中指定。

 按一下 [**屬性**] 視窗中的 [ **CorrelationData** ] 欄位以外的省略號按鈕或 [View ...] **InitializeCorrelation**活動設計工具介面上的提示文字會顯示 [**初始化相互關聯**] 對話方塊，您可以在其中指定相互關聯控制碼，以及用來初始化它的索引鍵/值組。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用這個對話方塊，請參閱 [型別集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md) 主題。

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 屬性
 下表顯示 <xref:System.ServiceModel.Activities.InitializeCorrelation> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在 [ **屬性** ] 視窗中或在介面上編輯 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動的易記名稱。 預設值為 InitializeCorrelation。<br /><br /> 雖然不是必須使用非預設值做為易記 <xref:System.Activities.Activity.DisplayName%2A>，但建議您盡量使用這類型的值。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|否|用於與相互關聯中工作流程活動相關聯的 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|否|相互關聯資料的字典，該字典會使訊息與工作流程執行個體產生關聯。<br /><br /> 使用 [ **初始化相互關聯** ] 對話方塊來設定 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> 。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用這個對話方塊，請參閱 [類型集合編輯器對話方塊](../workflow-designer/type-collection-editor-dialog-box.md) 主題。|

## <a name="see-also"></a>另請參閱
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [接收](../workflow-designer/receive-activity-designer.md) [receiveandsendreply]](../workflow-designer/receiveandsendreply-template-designer.md) [傳送](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)