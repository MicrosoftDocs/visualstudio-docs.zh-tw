---
title: 工作流程設計工具-Parallel 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2315c27bc0a35ac1dc839b5fd98003105d92bd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="parallel-activity-designer"></a>Parallel 活動設計工具

<xref:System.Activities.Statements.Parallel> 活動會並行執行屬於同一集合的子活動。

## <a name="the-parallel-activity"></a>Parallel 活動

<xref:System.Activities.Statements.Parallel> 活動會將它的子活動儲存在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。 如果某些子活動可能閒置，請使用 <xref:System.Activities.Statements.Parallel> 活動，而不是 <xref:System.Activities.Statements.Sequence> 活動。

<xref:System.Activities.Statements.Parallel>活動有<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>屬性，其中包含使用者指定的 Visual Basic 運算式。 在各個分支完成之後，<xref:System.Activities.Statements.Parallel> 活動會評估這個屬性。 如果評估為**True**，然後在<xref:System.Activities.Statements.Parallel>不會執行其他分支的活動完成。 如果<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>未評估成**True**，然後在<xref:System.Activities.Statements.Parallel>活動完成的所有子活動完成時。

### <a name="using-the-parallel-activity-designer"></a>使用 Parallel 活動設計工具

**平行**活動設計工具位於**控制流程**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤上的工作流程設計工具左側 (或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

**平行**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面上的活動設計工具通常用來放置，例如，內只要**順序**活動設計工具。 之後放入工作流程設計工具，它會建立<xref:System.Activities.Statements.Parallel>活動，其中預設包含<xref:System.Activities.Activity.DisplayName%2A>的**平行**

若要加入至活動<xref:System.Activities.Statements.Parallel.Branches%2A>平行活動的集合從一些其他活動設計工具拖曳**工具箱**拖內的三角形上**平行**活動設計工具。 三角形與分支內包含的活動相接。 可以重複這個程序來加入其他活動。 活動可以藉由拖放中將它們重新排列**平行**活動設計工具。

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Parallel 活動屬性

下表顯示 Parallel 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的易記顯示名稱。 預設值是**平行**。 這個值可以選擇性地編輯中**屬性**方格或直接在活動設計工具標頭。|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|包含要執行之子活動的集合。|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|在分支完成後評估。 如果評估為**True**，然後排定擱置中分支都會取消。 如果這個屬性未設定或評估為**False**，在活動完成的所有子活動完成時。 預設值是**null**。|

## <a name="see-also"></a>另請參閱

- [順序](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)