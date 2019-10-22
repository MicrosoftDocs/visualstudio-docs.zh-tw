---
title: 工作流程設計工具 If 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e0c08d655393a953e1abae9d33086d43e281500
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650230"
---
# <a name="if-activity-designer"></a>If 活動設計工具

<xref:System.Activities.Statements.If> 活動會評估條件，並且根據該評估的結果執行某個活動。 這個活動最適合用於使用程式設計的程序模型樣式時。 例如，<xref:System.Activities.Statements.If> 活動可巢狀置入 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Parallel> 活動內部。 如果您要使用 <xref:System.Activities.Statements.Flowchart> 活動，可以考慮改用 <xref:System.Activities.Statements.FlowDecision> 活動。

## <a name="if-properties-in-the-workflow-designer"></a>工作流程設計工具中的 If 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.If> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|判斷要執行哪個子活動的條件。 若要設定 <xref:System.Activities.Statements.If.Condition%2A>，請在 [ **If** ] 活動設計工具上或在屬性方格的 [**條件**] 方塊中，輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.If.Else%2A>|False|@No__t_0 為**false**時要執行的活動。 若要加入 <xref:System.Activities.Statements.If.Else%2A> 分支所執行的活動，請從 [工具箱] 將活動拖放到 [ **If** ] 活動設計**工具**上的 [ **Else** ] 方塊中，並加上提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.If.Then%2A>|False|當 <xref:System.Activities.Statements.If.Condition%2A> 為**true**時要執行的活動。 若要加入 <xref:System.Activities.Statements.If.Then%2A> 分支所執行的活動，請從 [工具箱] 將活動拖放到 [ **If** ] 活動設計**工具**上的 [ **Then** ] 方塊中，並加上提示文字「在此放置活動」。|

## <a name="see-also"></a>請參閱

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)