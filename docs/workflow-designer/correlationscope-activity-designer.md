---
title: 工作流程設計工具-CorrelationScope 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ca5955cae8d9b2cb1012e97f034d497bbc79e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949810"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 活動設計工具

**CorrelationScope**活動設計工具會用來建立及設定<xref:System.ServiceModel.Activities.CorrelationScope>活動，以提供使用的子系傳訊活動的隱含管理<xref:System.ServiceModel.Activities.CorrelationHandle>物件。

## <a name="the-correlationscope-activity"></a>CorrelationScope 活動

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 屬性會指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 包含在 <xref:System.ServiceModel.Activities.Send> 中的 <xref:System.ServiceModel.Activities.Receive> 與 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 活動，會設定為使用包含之 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 活動的 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性來執行相互關聯。

### <a name="use-the-correlationscope-activity-designer"></a>使用 CorrelationScope 活動設計工具

**CorrelationScope**活動設計工具可在**Messaging**分類**工具箱**，即可存取的哪一個**工具箱**工作流程設計工具左側的索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**CorrelationScope**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面。 這會建立<xref:System.ServiceModel.Activities.CorrelationScope>活動，具有預設值**DisplayName** CorrelationScope。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**CorrelationScope**活動設計工具或**DisplayName**方塊**屬性**視窗。

若要指定<xref:System.ServiceModel.Activities.CorrelationHandle>的子系傳訊活動使用，選取旁邊的省略符號按鈕**CorrelatesWith**欄位中**屬性**視窗，以顯示**運算式編輯器** 對話方塊。 這個屬性也可以在活動設計工具介面上設定。

範圍內的相互關聯的活動由卸除其設計工具內**主體**方塊內**CorrelationScope**設計工具。

### <a name="the-correlationscope-properties"></a>CorrelationScope 屬性

下表顯示 <xref:System.ServiceModel.Activities.CorrelationScope> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在編輯**屬性**視窗或在工作流程設計工具介面中，且經常在。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 活動可選用的易記名稱。|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|指定用來管理子系傳訊活動的 <xref:System.ServiceModel.Activities.CorrelationHandle>。 如果沒有設定這個屬性，<xref:System.ServiceModel.Activities.CorrelationScope> 會自動建立隱含 <xref:System.ServiceModel.Activities.CorrelationHandle>。|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|指定相互關聯範圍內的活動。|

## <a name="see-also"></a>另請參閱

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)