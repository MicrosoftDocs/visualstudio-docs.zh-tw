---
title: Parallel 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672641"
---
# <a name="parallel-activity-designer"></a>Parallel 活動設計工具
<xref:System.Activities.Statements.Parallel> 活動會並行執行屬於同一集合的子活動。

## <a name="the-parallel-activity"></a>Parallel 活動
 <xref:System.Activities.Statements.Parallel> 活動會將它的子活動儲存在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。 如果某些子活動可能閒置，請使用 <xref:System.Activities.Statements.Parallel> 活動，而不是 <xref:System.Activities.Statements.Sequence> 活動。

 <xref:System.Activities.Statements.Parallel> 活動有一個 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 屬性，其中包含使用者指定的 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 運算式。 在各個分支完成之後，<xref:System.Activities.Statements.Parallel> 活動會評估這個屬性。 如果評估為**True**，則 <xref:System.Activities.Statements.Parallel> 活動會完成，而不會執行其他分支。 如果 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 未評估為**True**，則 <xref:System.Activities.Statements.Parallel> 活動會在所有子活動完成時完成。

### <a name="using-the-parallel-activity-designer"></a>使用 Parallel 活動設計工具
 [ **Parallel** ] 活動設計**工具**位於 [工具箱] 的 [**控制流程**] 分類中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 左側的 [**工具箱**] 索引標籤（也可以選取 [ **工具列]，從[View** ] 功能表，或 CTRL + ALT + X）。

 [ **Parallel** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動設計工具的任一處，例如在 [ **Sequence** ] 活動設計工具內。 將它放入 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 之後，它會建立 <xref:System.Activities.Statements.Parallel> 活動，其預設會包含**平行**<xref:System.Activities.Activity.DisplayName%2A>

 若要將活動加入至 parallel 活動的 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合，請將一些其他活動設計工具從 [工具箱] 拖曳至 [ **parallel** ] 活動設計**工具**內的三角形上。 三角形與分支內包含的活動相接。 可以重複這個程序來加入其他活動。 藉由在 [ **Parallel** ] 活動設計工具內拖放活動，即可重新排列它們。

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Parallel 活動屬性
 下表顯示 Parallel 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的易記顯示名稱。 預設值為**Parallel**。 您可以在 [**屬性**] 方格中或直接在活動設計工具標頭上，選擇性地編輯此值。|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|包含要執行之子活動的集合。|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|在分支完成後評估。 如果評估為**True**，則會取消已排程的擱置中分支。 如果此屬性未設定或評估為**False**，則活動會在所有子活動完成時完成。 預設值為**null**。|

## <a name="see-also"></a>請參閱
 [順序](../workflow-designer/sequence-activity-designer.md) [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [控制流程](../workflow-designer/control-flow-activity-designers.md)