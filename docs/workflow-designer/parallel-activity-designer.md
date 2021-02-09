---
title: 工作流程設計工具平行活動設計工具
description: 深入瞭解平行活動，以及如何使用 Parallel 活動設計工具同時執行子活動的集合。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3997b72105c22f10500559370d8a23faaa2f24eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905169"
---
# <a name="parallel-activity-designer"></a>Parallel 活動設計工具

<xref:System.Activities.Statements.Parallel> 活動會並行執行屬於同一集合的子活動。

## <a name="the-parallel-activity"></a>Parallel 活動

<xref:System.Activities.Statements.Parallel> 活動會將它的子活動儲存在 <xref:System.Activities.Statements.Parallel.Branches%2A> 集合中。 如果某些子活動可能閒置，請使用 <xref:System.Activities.Statements.Parallel> 活動，而不是 <xref:System.Activities.Statements.Sequence> 活動。

<xref:System.Activities.Statements.Parallel>活動具有 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 屬性，該屬性包含 Visual Basic 運算式指定的使用者。 在各個分支完成之後，<xref:System.Activities.Statements.Parallel> 活動會評估這個屬性。 如果評估為 **True**，則 <xref:System.Activities.Statements.Parallel> 活動會完成，而不會執行其他分支。 如果 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 未評估為 **True**，則 <xref:System.Activities.Statements.Parallel> 活動會在所有子活動都已完成時完成。

### <a name="using-the-parallel-activity-designer"></a>使用 Parallel 活動設計工具

存取 [工具箱] 的 [**控制流程**] 類別中的 [ **Parallel** ] 活動設計 **工具**。

[ **Parallel** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上，通常用來放置活動設計工具的任一處，例如在 [ **Sequence** ] 活動設計工具內部。 將它放入工作流程設計工具之後，它會建立 <xref:System.Activities.Statements.Parallel> 活動，此活動預設包含 <xref:System.Activities.Activity.DisplayName%2A> **Parallel** 的

若要將活動加入至 <xref:System.Activities.Statements.Parallel.Branches%2A> parallel 活動的集合中，請從 [工具箱] 將其他活動設計工具拖曳至 [ **parallel** ] 活動設計 **工具** 內的三角形上。 三角形與分支內包含的活動相接。 可以重複這個程序來加入其他活動。 您可以將活動拖放到 [ **Parallel** ] 活動設計工具中，以重新排序活動。

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Parallel 活動屬性

下表顯示 Parallel 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定活動設計工具在標頭中的易記顯示名稱。 預設值為 **Parallel**。 您可以選擇性地在 **屬性** 方格中或直接在活動設計工具標頭上編輯此值。|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|是|包含要執行之子活動的集合。|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|否|在分支完成後評估。 如果評估為 **True**，則會取消已排程的擱置中分支。 如果這個屬性未設定或評估為 **False**，則活動會在所有子活動都已完成時完成。 預設值為 **null**。|

## <a name="see-also"></a>另請參閱

- [序列](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)
