---
title: 工作流程設計工具 FlowSwitch &lt; T &gt; 活動設計工具
description: 瞭解 FlowSwitch <T> 活動是條件式節點，它會根據比對準則提供控制流程的分支。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f61dd3f14ba527e9f5be0e009825902e683fb1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876559"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T> 活動設計工具

<xref:System.Activities.Statements.FlowSwitch%601> 活動是條件式節點，當需要兩個以上的替代分支時，該節點會根據相符的準則提供控制流程的分支。 如果流程分支僅需要兩個路徑，請改用 <xref:System.Activities.Statements.FlowDecision> 活動。

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T> 活動

<xref:System.Activities.Statements.FlowSwitch%601>活動包含，其 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 會傳回泛型參數) 在評估時所指定之類型 *T* (的值。 活動也包含一組 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>，這會指定從這個評估的可能結果到一組 <xref:System.Activities.Statements.FlowNode> 物件的唯一對應。 <xref:System.Activities.Statements.FlowNode>執行的是其類型為 *T* 的物件符合評估之值的物件 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 。 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> 案例可 (選擇性) 地提供給未取得相符結果的案例。

### <a name="using-the-flowswitcht-activity-designer"></a>使用 FlowSwitch \<T> 活動設計工具

[ **FlowSwitch \<T>** ] 活動設計 **工具** 位於 [工具箱] 的 [**流程圖**] 類別中，若要存取，請按一下工作流程設計工具左側的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

[ **FlowSwitch \<T>** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [ **Flowchart** ] 活動設計工具內的工作流程設計工具介面上。 使用顯示的 [ **選取類型** ] 視窗，即可指定與程式碼中的程式碼相關聯的類型 (， <xref:System.Activities.Statements.FlowSwitch%601> 其泛型參數) 從評估來取得 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 。 此程式會在 <xref:System.Activities.Statements.FlowSwitch%601> 活動內建立標示為 **切換** 的活動 <xref:System.Activities.Statements.Flowchart> 。 您 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 可以在 [**屬性**] 視窗的 [**運算式**] 方塊中，按一下提示文字顯示為 [輸入 VB 運算式] 的位置，以輸入。

將滑鼠移到 [ **FlowSwitch \<T>** ] 活動設計工具上，讓用來連結的正方形控點 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 出現在邊緣周圍。 將 **FlowSwitch<T \>** 活動設計工具和其他活動設計工具拖曳到 **流程圖** 之後， <xref:System.Activities.Activity> 它們所代表的物件就可以連結在一起，以指定執行順序。 若要建立 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 與相關聯的其中一個 <xref:System.Activities.Statements.FlowSwitch%601> ，請在 **FlowSwitch<T \>** 的周邊，按一下其中一個方形案例控點，然後按住滑鼠) 按鈕，將其拖曳 (，方法是將滑鼠停留在其設計工具上時，將滑鼠停留在目的地活動周圍的其中一個控點。 放開滑鼠按鍵， **FlowSwitch<T \>** 的箭號會出現在目的地設計工具中，表示此案例。 此案例的預設值會顯示在箭號上，而且可以在 [**屬性**] 視窗的 [**案例**] 方塊中編輯。

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T> 屬性

下表顯示 <xref:System.Activities.Statements.FlowSwitch%601> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|是|指定已評估的運算式，以判斷要將哪一個 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 切換到執行路徑。|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|否|指定從評估<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 所取得的可能結果到一組<xref:System.Activities.Statements.FlowNode> 物件的唯一對應。|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|是|指定對應，時機是當 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 的評估結果與包含於 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 物件的值不相符時。|

## <a name="see-also"></a>另請參閱

- [流程圖](../workflow-designer/flowchart-activity-designers.md)
- [流程圖](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
