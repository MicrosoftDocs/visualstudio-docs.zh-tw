---
title: "控制流程活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 45ffc19d3ede7af9d32e4599f17ecde9bd097bb7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="control-flow-activity-designers"></a>Control Flow 活動設計工具
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 包括幾項系統提供的活動，在您建構工作流程時，可以使用這些活動。 本節包含用來控制工作流程中之流程的系統提供活動。 下列主題說明會這些活動，並且提供如何使用的指引。  
  
## <a name="in-this-section"></a>本章節內容  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 執行其主體包含至少一次，直到指定的條件評估為該活動**true**。  
  
 [ForEach\<T >](http://msdn.microsoft.com/en-us/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 針對指定集合中的各個項目，執行其主體包含的活動。  
  
 [If](../workflow-designer/if-activity-designer.md)  
 評估條件，並且根據該評估的結果執行某個活動。  
  
 [平行](../workflow-designer/parallel-activity-designer.md)  
 同時執行屬於同一集合的子活動。  
  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)  
 列舉集合項目，並針對集合的每個項目平行執行內嵌陳述式。  
  
 [挑選](../workflow-designer/pick-activity-designer.md)  
 根據某個事件提供以事件為主的流程控制，執行若干分支的其中一個做為回應。  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 提供在 <xref:System.Activities.Statements.Pick> 活動內執行的潛在路徑。  
  
 [順序](../workflow-designer/sequence-activity-designer.md)  
 包含子活動的有序集合，該集合會依序執行。  
  
 [交換器\<T >](http://msdn.microsoft.com/en-us/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 評估指定的運算式，並且根據關聯索引鍵符合求值結果的多個活動，從這些活動的集合中執行該活動。  
  
 [While](../workflow-designer/while-activity-designer.md)  
 執行時指定的條件評估為其主體中包含的活動**true**。  
  
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
  
 [訊息處理](../workflow-designer/messaging-activity-designers.md)  
  
 [執行階段](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [異動](../workflow-designer/transaction-activity-designers.md)  
  
 [集合](../workflow-designer/collection-activity-designers.md)  
  
 [錯誤處理](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>外部資源  
 [使用活動設計工具](../workflow-designer/using-the-activity-designers.md)