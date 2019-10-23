---
title: 控制流程活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f17913864f80e04c3e8b8e703f057094c9bdea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656933"
---
# <a name="control-flow-activity-designers"></a>Control Flow 活動設計工具
[!INCLUDE[wfd1](../includes/wfd1-md.md)] 包含一些系統提供的活動，可供您在建立工作流程時使用。 本節包含用來控制工作流程中之流程的系統提供活動。 下列主題說明會這些活動，並且提供如何使用的指引。

## <a name="in-this-section"></a>本節內容
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)執行其主體所包含的活動至少一次，直到指定的條件評估為**true**為止。

 [ForEach \<T >](foreach-t-activity-designer.md)針對指定集合中的每個專案，執行其主體中包含的活動。

 [If](../workflow-designer/if-activity-designer.md)評估條件，並根據該評估的結果執行活動。

 [平行](../workflow-designer/parallel-activity-designer.md)同時執行子活動的集合。

 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md)列舉集合的元素，並平行執行集合中每個元素的內嵌語句

 [挑選](../workflow-designer/pick-activity-designer.md)會執行數個分支中的其中一個，以回應一些提供事件型流量控制的事件。

 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)提供在 <xref:System.Activities.Statements.Pick> 活動內執行的潛在路徑。

 [順序](../workflow-designer/sequence-activity-designer.md)包含依序執行之子活動的已排序集合。

 [切換 \<T >](switch-t-activity-designer.md)評估指定的運算式，並從活動集合執行活動，其相關聯的索引鍵符合從評估取得的值。

 [While](../workflow-designer/while-activity-designer.md)當指定的條件評估為**true**時，執行其主體中所包含的活動。

## <a name="reference"></a>參考資料
 <xref:System.Activities.Activity>

 <xref:System.Activities.Statements.DoWhile>

 <xref:System.Activities.Statements.ForEach%601>

 <xref:System.Activities.Statements.If>

 <xref:System.Activities.Statements.Parallel>

 <xref:System.Activities.Statements.ParallelForEach%601>

 <xref:System.Activities.Statements.Pick>

 <xref:System.Activities.Statements.PickBranch>

 <xref:System.Activities.Statements.Sequence>

 <xref:System.Activities.Statements.Switch%601>

 <xref:System.Activities.Statements.While>

## <a name="related-sections"></a>相關章節
 如需其他活動設計工具類型的資訊，請參閱下列主題。

 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)

 [流程圖](../workflow-designer/flowchart-activity-designers.md)

 [Messaging](../workflow-designer/messaging-activity-designers.md)

 [執行階段](../workflow-designer/runtime-activity-designers.md)

 [Primitives](../workflow-designer/primitives-activity-designers.md)

 [異動](../workflow-designer/transaction-activity-designers.md)

 [集合](../workflow-designer/collection-activity-designers.md)

 [錯誤處理](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>外部資源
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)