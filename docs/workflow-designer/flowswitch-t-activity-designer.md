---
title: 工作流程設計工具-FlowSwitch <T> 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f167f46a2ed118e8781f66e4a781d4a3ef95b0d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650399"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch \<T > 活動設計工具

<xref:System.Activities.Statements.FlowSwitch%601> 活動是條件式節點，當需要兩個以上的替代分支時，該節點會根據相符的準則提供控制流程的分支。 如果流程分支僅需要兩個路徑，請改用 <xref:System.Activities.Statements.FlowDecision> 活動。

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T > 活動

@No__t_0 活動包含 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>，其會在評估時傳回*t*類型的值（由泛型參數指定）。 活動也包含一組 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，這會指定從這個評估的可能結果到一組 <xref:System.Activities.Statements.FlowNode> 物件的唯一對應。 @No__t_0 執行的是，其物件的類型*t*符合評估 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的值。 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> 案例可 (選擇性) 地提供給未取得相符結果的案例。

### <a name="using-the-flowswitcht-activity-designer"></a>使用 FlowSwitch \<T > 活動設計工具

[ **FlowSwitch \<T >** ] 活動設計**工具**位於 [工具箱] 的 [**流程圖**] 類別中，若要存取，請按一下工作流程設計工具左側的 [**工具箱**] 索引標籤。 或者，從  **View**  功能表中選取 **工具箱**，或按**Ctrl** +**Alt** +**X**。

[ **FlowSwitch \<T >** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [ **Flowchart** ] 活動設計工具內的工作流程設計工具介面上。 使用顯示的 [**選取類型**] 視窗，即可指定從評估 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 取得的類型（在程式碼中，與其泛型參數的 <xref:System.Activities.Statements.FlowSwitch%601> 相關聯）。 此程式會在 <xref:System.Activities.Statements.Flowchart> 活動內建立標示為**Switch**的 <xref:System.Activities.Statements.FlowSwitch%601> 活動。 您可以在 [**屬性**] 視窗的 [**運算式**] 方塊中輸入 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>，方法是按一下提示文字顯示「輸入 VB 運算式」的位置。

將滑鼠移至 [ **FlowSwitch \<T >** ] 活動設計工具上，使用來連結 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 的方形控點會出現在其邊緣周圍。 將**FlowSwitch < T \>** 活動設計工具和其他活動設計工具拖曳至**流程圖**之後，它們所代表的 <xref:System.Activities.Activity> 物件就可以連結在一起，以指定執行的順序。 若要建立與 <xref:System.Activities.Statements.FlowSwitch%601> 相關聯的其中一個 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，請按一下**FlowSwitch < t \>** 周邊的其中一個正方形 case 控點，並將它拖曳（按住滑鼠按鍵）至其中一個以類似方式出現在其中的控點當滑鼠停留在其設計工具上時的目的地活動。 放開滑鼠按鍵，然後從**FlowSwitch < T \>** 到目的地設計工具的箭號，就會顯示此案例。 此案例的預設值會顯示在箭號上，而且可以在 [**屬性**] 視窗的 [**案例**] 方塊中編輯。

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T > 屬性

下表顯示 <xref:System.Activities.Statements.FlowSwitch%601> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|指定已評估的運算式，以判斷要將哪一個 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 切換到執行路徑。|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|指定從評估<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 所取得的可能結果到一組<xref:System.Activities.Statements.FlowNode> 物件的唯一對應。|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|指定對應，時機是當 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的評估結果與包含於 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 物件的值不相符時。|

## <a name="see-also"></a>請參閱

- [流程圖](../workflow-designer/flowchart-activity-designers.md)
- [流程圖](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)