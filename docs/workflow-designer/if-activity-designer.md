---
title: 工作流程設計工具-如果活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 716f2b13758864d5eda449967990f9e5be399a9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822836"
---
# <a name="if-activity-designer"></a>If 活動設計工具

<xref:System.Activities.Statements.If> 活動會評估條件，並且根據該評估的結果執行某個活動。 這個活動最適合用於使用程式設計的程序模型樣式時。 例如，<xref:System.Activities.Statements.If> 活動可巢狀置入 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Parallel> 活動內部。 如果您要使用 <xref:System.Activities.Statements.Flowchart> 活動，可以考慮改用 <xref:System.Activities.Statements.FlowDecision> 活動。

## <a name="if-properties-in-the-workflow-designer"></a>工作流程設計工具中的 If 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.If> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|判斷要執行哪個子活動的條件。 若要設定<xref:System.Activities.Statements.If.Condition%2A>，輸入在 Visual Basic 運算式**條件**方塊**如果**活動設計工具上或在屬性方格中。|
|<xref:System.Activities.Statements.If.Else%2A>|False|執行活動<xref:System.Activities.Statements.If.Condition%2A>已**false**。 將執行的活動新增<xref:System.Activities.Statements.If.Else%2A>分支中，卸除的活動**工具箱**成**Else**方塊**如果**活動設計工具提示文字與"在此放置活動 」。|
|<xref:System.Activities.Statements.If.Then%2A>|False|執行活動<xref:System.Activities.Statements.If.Condition%2A>已 **，則為 true**。 將執行的活動新增<xref:System.Activities.Statements.If.Then%2A>分支中，卸除的活動**工具箱**成**然後**方塊**如果**活動設計工具提示文字與"在此放置活動 」。|

## <a name="see-also"></a>另請參閱

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)