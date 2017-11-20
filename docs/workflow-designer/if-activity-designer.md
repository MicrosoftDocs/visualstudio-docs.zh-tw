---
title: "如果活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d3928330558c3d611decd2a87498d33fd6482ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="if-activity-designer"></a>If 活動設計工具
<xref:System.Activities.Statements.If> 活動會評估條件，並且根據該評估的結果執行某個活動。 這個活動最適合用於使用程式設計的程序模型樣式時。 例如，<xref:System.Activities.Statements.If> 活動可巢狀置入 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Parallel> 活動內部。 如果您要使用 <xref:System.Activities.Statements.Flowchart> 活動，可以考慮改用 <xref:System.Activities.Statements.FlowDecision> 活動。  
  
## <a name="if-properties-in-the-workflow-designer"></a>工作流程設計工具中的 If 屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.If> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|判斷要執行哪個子活動的條件。 若要設定<xref:System.Activities.Statements.If.Condition%2A>，輸入[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]中的運算式**條件**方塊**如果**活動設計工具，或在屬性方格中。|  
|<xref:System.Activities.Statements.If.Else%2A>|False|要執行的活動<xref:System.Activities.Statements.If.Condition%2A>是**false**。 若要加入活動所執行的<xref:System.Activities.Statements.If.Else%2A>分支、 卸除的活動**工具箱**到**Else**方塊上**如果**活動設計工具提示文字的"在此置放活動 」。|  
|<xref:System.Activities.Statements.If.Then%2A>|False|要執行的活動<xref:System.Activities.Statements.If.Condition%2A>是**true**。 若要加入活動所執行的<xref:System.Activities.Statements.If.Then%2A>分支、 卸除的活動**工具箱**到**然後**方塊上**如果**活動設計工具提示文字的"在此置放活動 」。|  
  
## <a name="see-also"></a>另請參閱  
 [順序](../workflow-designer/sequence-activity-designer.md)   
 [平行](../workflow-designer/parallel-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)