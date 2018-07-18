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
ms.openlocfilehash: 3c4f10b9bb564268f5aeee59d871fd44324097cc
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756672"
---
# <a name="parallel-activity-designer"></a>Parallel 活動設計工具

<xref:System.Activities.Statements.Parallel> 活動會並行執行屬於同一集合的子活動。

## <a name="the-parallel-activity"></a>Parallel 活動

<xref:System.Activities.Statements.Parallel> 活動會將它的子活動儲存在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。 如果某些子活動可能閒置，請使用 <xref:System.Activities.Statements.Parallel> 活動，而不是 <xref:System.Activities.Statements.Sequence> 活動。

<xref:System.Activities.Statements.Parallel>活動具有<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>屬性，其中包含使用者指定 Visual Basic 運算式。 在各個分支完成之後，<xref:System.Activities.Statements.Parallel> 活動會評估這個屬性。 如果評估為 **，則為 True**，然後在<xref:System.Activities.Statements.Parallel>活動完成且沒有執行其他分支。 如果<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>不會評估 **，則為 True**，然後在<xref:System.Activities.Statements.Parallel>活動完成的所有子活動完成時。

### <a name="using-the-parallel-activity-designer"></a>使用 Parallel 活動設計工具

存取權**平行**中的活動設計工具**控制流程**分類**工具箱**。

**平行**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，只要活動設計工具通常用來放置，比方說，內**順序**活動設計工具。 後放入工作流程設計工具，它會建立<xref:System.Activities.Statements.Parallel>活動，其中預設包含<xref:System.Activities.Activity.DisplayName%2A>的**平行**

若要加入至活動<xref:System.Activities.Statements.Parallel.Branches%2A>集合的平行活動中，從一些其他活動設計工具拖曳**工具箱**並將它放在三角形**平行**活動設計工具。 三角形與分支內包含的活動相接。 可以重複這個程序來加入其他活動。 活動可以藉由拖放內重新排列**平行**活動設計工具。

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Parallel 活動屬性

下表顯示 Parallel 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的易記顯示名稱。 預設值是**平行**。 值可以在中選擇性地編輯**屬性**方格或直接在活動設計工具標頭。|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|包含要執行之子活動的集合。|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|在分支完成後評估。 如果評估為 **，則為 True**，然後排定取消擱置中分支。 如果這個屬性未設定或是評估為**False**，在活動完成的所有子活動完成時。 預設值是**null**。|

## <a name="see-also"></a>另請參閱

- [順序](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)