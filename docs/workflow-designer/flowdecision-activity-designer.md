---
title: 工作流程設計工具 FlowDecision 活動設計工具
description: 瞭解 FlowDecision 節點是條件式節點，它會提供控制流程的分支，以提供兩種替代方案的其中一種。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77570557563b4aca3109f5bcbdebd16c7af09144
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938430"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision 活動設計工具

<xref:System.Activities.Statements.FlowDecision> 節點是條件式節點，會根據是否滿足指定條件來提供控制流程的二選一分支。 如果流程要求兩個以上的分支，請改用 <xref:System.Activities.Statements.FlowSwitch%601>。

## <a name="the-flowdecision-node"></a>FlowDecision 節點

當流程可分支為兩個路徑時，請使用 <xref:System.Activities.Statements.FlowDecision>。 <xref:System.Activities.Statements.FlowDecision> 節點有 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 以及與以下兩種可能結果之一相關聯的 <xref:System.Activities.Statements.FlowNode>：<xref:System.Activities.Statements.FlowDecision.True%2A> 或 <xref:System.Activities.Statements.FlowDecision.False%2A>。 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 會加以評估，且此評估的值會判斷在 <xref:System.Activities.Statements.FlowNode> 內要處理的下一個 <xref:System.Activities.Statements.Flowchart>。

### <a name="using-the-flowdecision-designer"></a>使用 FlowDecision 設計工具

[ **FlowDecision** ] 設計工具位於 [**工具箱**] 的 [**流程圖**] 類別中，若要存取，請按一下工作流程設計工具上的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

**FlowDecision** 設計工具可以從 [工具箱] 拖曳出來，放到 [ **Flowchart** ] 活動設計 **工具** 內的工作流程設計工具介面上。 這會在 <xref:System.Activities.Statements.FlowDecision> 活動中建立加上標籤的 **決策** <xref:System.Activities.Statements.Flowchart> 。 滑鼠移到設計工具上，會出現兩個分支的 **True** 和 **False** 方形控點。

將 **FlowDecision** 設計工具和其他設計工具拖曳至 **流程圖** 之後，可將節點連結在一起，以指定執行順序。 若要建立來源節點之間的連結 (包括 **FlowDecision**) 和目的地節點的 **True** 和 **False** 分支，請將滑鼠游標移到來源節點的設計工具上，正方形控點會出現在其每一側。 按一下方形控點，按住滑鼠按鈕加以拖曳到目的地節點中的另一個控點，此控點是當滑鼠游標移到目的地活動的設計工具上時，以相似方式顯示的控點。 放開滑鼠按鈕，這兩個節點之間就會建立連結，此連結會以箭號表示，從來源設計工具指向目的地設計工具。

在 <xref:System.Activities.Statements.FlowDecision.Condition%2A> [**屬性**] 視窗的 [條件] 方塊中，按一下提示文字會顯示「輸入 VB 運算式」的位置，即可在 [屬性] 視窗的 [**條件**] 方塊中輸入運算式。

### <a name="the-flowdecision-properties"></a>FlowDecision 屬性

下表顯示 <xref:System.Activities.Statements.FlowDecision> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|是|判斷流程控制要採取的條件限制。|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|否|如果滿足 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的條件，則由流程控制採取的路徑。|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|否|如果不滿足 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 的條件，則由流程控制採取的路徑。|

## <a name="see-also"></a>另請參閱

- [流程圖](../workflow-designer/flowchart-activity-designers.md)
- [流程圖](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
