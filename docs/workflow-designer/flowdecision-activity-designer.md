---
title: FlowDecision 活動設計工具 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fccddd294b11b6d7c4eee7f48fa00b77b1148717
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="flowdecision-activity-designer"></a>FlowDecision 活動設計工具
<xref:System.Activities.Statements.FlowDecision> 節點是條件式節點，會根據是否滿足指定條件來提供控制流程的二選一分支。 如果流程要求兩個以上的分支，請改用 <xref:System.Activities.Statements.FlowSwitch%601>。

## <a name="the-flowdecision-node"></a>FlowDecision 節點
 當流程可分支為兩個路徑時，請使用 <xref:System.Activities.Statements.FlowDecision>。 <xref:System.Activities.Statements.FlowDecision> 節點有 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 以及與以下兩種可能結果之一相關聯的 <xref:System.Activities.Statements.FlowNode>：<xref:System.Activities.Statements.FlowDecision.True%2A> 或 <xref:System.Activities.Statements.FlowDecision.False%2A>。 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 會加以評估，且此評估的值會判斷在 <xref:System.Activities.Statements.FlowNode> 內要處理的下一個 <xref:System.Activities.Statements.Flowchart>。

### <a name="using-the-flowdecision-designer"></a>使用 FlowDecision 設計工具
 **FlowDecision**設計工具位於**流程圖**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **FlowDecision**設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面內**流程圖**活動設計工具。 這會建立<xref:System.Activities.Statements.FlowDecision>標示為**決策**內<xref:System.Activities.Statements.Flowchart>活動。 滑鼠停留在設計工具和**True**和**False**出現兩個分支的方形控點。

 拖曳之後**FlowDecision**設計工具和其他設計工具到**流程圖**，節點可以連結在一起，以指定的執行順序。 若要建立來源節點間的連結 (包括**True**和**False**的分支**FlowDecision**) 與目的地節點，滑鼠停留在來源節點的設計工具和它的每一端上出現方形控點。 按一下方形控點，按住滑鼠按鈕加以拖曳到目的地節點中的另一個控點，此控點是當滑鼠游標移到目的地活動的設計工具上時，以相似方式顯示的控點。 放開滑鼠按鈕，這兩個節點之間就會建立連結，此連結會以箭號表示，從來源設計工具指向目的地設計工具。

 狀態運算式<xref:System.Activities.Statements.FlowDecision.Condition%2A>可以依照輸入**條件**方塊**屬性**按一下的視窗上提示文字該處會指示 「 輸入 VB 運算式 」。

### <a name="the-flowdecision-properties"></a>FlowDecision 屬性
 下表顯示 <xref:System.Activities.Statements.FlowDecision> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|判斷流程控制要採取的條件限制。|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|如果滿足 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的條件，則由流程控制採取的路徑。|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|如果不滿足 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的條件，則由流程控制採取的路徑。|

## <a name="see-also"></a>另請參閱

- [流程圖](../workflow-designer/flowchart-activity-designers.md)
- [流程圖](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)