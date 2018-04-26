---
title: 工作流程設計工具-FlowSwitch<T>活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45c655987f3cafd77b284d9d11eafefd56a188fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T > 活動設計工具

<xref:System.Activities.Statements.FlowSwitch%601> 活動是條件式節點，當需要兩個以上的替代分支時，該節點會根據相符的準則提供控制流程的分支。 如果流程分支僅需要兩個路徑，請改用 <xref:System.Activities.Statements.FlowDecision> 活動。

## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > 活動

<xref:System.Activities.Statements.FlowSwitch%601>活動包含<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>傳回型別的值*T* （由泛型參數指定） 時進行評估。 活動也包含一組 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，這會指定從這個評估的可能結果到一組 <xref:System.Activities.Statements.FlowNode> 物件的唯一對應。 <xref:System.Activities.Statements.FlowNode>已執行之物件的型別*T*的評估值<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>。 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> 案例可 (選擇性) 地提供給未取得相符結果的案例。

### <a name="using-the-flowswitcht-activity-designer"></a>使用 FlowSwitch\<T > 活動設計工具

**FlowSwitch\<T >** 活動設計工具位於**流程圖**分類的**工具箱**，依序按一下存取的哪一個**工具箱** 索引標籤上的工作流程設計工具左側 (或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

**FlowSwitch\<T >** 活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面內**流程圖**活動設計工具。 使用**選取型別**視窗會顯示指定的型別 (相關聯的程式碼中<xref:System.Activities.Statements.FlowSwitch%601>藉由其泛型參數) 取自評估<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>。 這個程序建立<xref:System.Activities.Statements.FlowSwitch%601>活動標示為**交換器**內<xref:System.Activities.Statements.Flowchart>活動。 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>可以依照輸入**運算式**方塊**屬性**按一下的視窗上提示文字該處會指示 「 輸入 VB 運算式 」。

將滑鼠移**FlowSwitch\<T >** 活動設計工具用來連結的方形控點<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>來顯示其邊緣。 拖曳之後**FlowSwitch < T\>** 活動設計工具和其他活動設計工具到**流程圖**、<xref:System.Activities.Activity>它們代表的物件已經準備好連結在一起若要指定執行順序。 若要建立的其中一個<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>聯<xref:System.Activities.Statements.FlowSwitch%601>，按一下其中一個方形案例控點的周邊網路上**FlowSwitch < T\>** 並將它拖曳 （按住滑鼠按鈕） 以其中一個控點以類似的方式在目的地活動周圍時出現的滑鼠停留在其設計工具。 放開滑鼠按鈕以及從箭頭**FlowSwitch < T\>** 至目的地設計工具會顯示表示此案例。 預設值，這個案例顯示在箭號，而且可以在編輯**案例**方塊**屬性**視窗。

### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > 屬性

下表顯示 <xref:System.Activities.Statements.FlowSwitch%601> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|指定已評估的運算式，以判斷要將哪一個 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 切換到執行路徑。|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|指定從評估<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 所取得的可能結果到一組<xref:System.Activities.Statements.FlowNode> 物件的唯一對應。|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|指定對應，時機是當 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的評估結果與包含於 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 物件的值不相符時。|

## <a name="see-also"></a>另請參閱

- [流程圖](../workflow-designer/flowchart-activity-designers.md)
- [流程圖](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)