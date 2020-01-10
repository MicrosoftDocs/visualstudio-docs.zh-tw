---
title: 工作流程設計工具-Flowchart 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d786e9acfa99d2b106b72822a0106e2161724790
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597031"
---
# <a name="flowchart-activity-designer"></a>Flowchart 活動設計工具

<xref:System.Activities.Statements.Flowchart> 活動會用來建立工作流程，這些工作流程可定義及管理複雜的流程控制。 <xref:System.Activities.Statements.Flowchart> 可以透過程式碼或使用工作流程設計工具來撰寫。 本主題記載工作流程設計工具體驗。 工作流程設計工具工作流程活動設計工具可讓開發人員以自然的方式撰寫工作流程。

## <a name="the-flowchart-activity"></a>Flowchart 活動

<xref:System.Activities.Statements.Flowchart> 指定工作流程開始時會執行的唯一 <xref:System.Activities.Statements.Flowchart.StartNode%2A>，並且使用已連結 <xref:System.Activities.Statements.Flowchart.Nodes%2A> 的網路來建立任意迴圈，或是在任何特定時間將執行的流動轉向任何其他地方。

### <a name="using-the-flowchart-activity-designer"></a>使用 Flowchart 活動設計工具

**Flowchart**  活動設計工具位於 **工具箱** 的 **流程圖** 類別中，若要存取，請按一下 工作流程設計工具上的 **工具箱** 索引標籤。 或者，從  **View**  功能表中選取 **工具箱**，或按**Ctrl**+**Alt**+**X**。

[ **Flowchart** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上，通常用來放置活動設計工具的任一處，以做為根活動或做為另一個控制流程活動的子系。 如果將 [ **Flowchart** ] 活動設計工具放到空白的工作流程設計工具介面上，它會建立 <xref:System.Activities.Statements.Flowchart> 活動，其預設會在展開的視圖中顯示，其中起始執行的開始節點會表示為綠色球。 如果將 [ **Flowchart** ] 活動設計工具拖放到另一個 [控制流程] 活動中，它會在最小化的視圖中呈現其本身，只要按兩下 [ **Flowchart** ] 活動設計工具即可展開。 [工具箱] 中的任何活動都可以直接拖曳到 [ **Flowchart** ] 活動設計**工具**上，包括其他控制流程活動。

將各種活動設計工具拖曳至工作流程設計工具畫布上之後，它們所代表的 <xref:System.Activities.Activity> 物件可以連結在一起，以指定執行的順序。 若要建立來源活動與目的地活動之間的連結，請將滑鼠游標移至來源活動的設計工具上，設計工具的每一邊就會出現方形控點。 按一下方形控點，按住滑鼠按鈕，拖曳到目的地活動周圍的其中一個控點，亦即將滑鼠游標移至目的地活動上時同樣會出現的幾個控點之一。 放開滑鼠按鈕，這兩個活動之間就會建立連結，此連結會以箭號表示，從來源設計工具指向目的地設計工具。

### <a name="flowchart-activity-properties"></a>Flowchart 活動屬性

下表顯示 <xref:System.Activities.Statements.Flowchart> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|內容名稱|必要|使用|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定活動設計工具在標頭中的顯示名稱。 預設值為 Flowchart。 此值可以在 [**屬性**] 視窗中編輯，或直接在活動設計工具標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|設定至這個 <xref:System.Activities.Statements.Flowchart> 的範圍內，使其子活動都有共同狀態之變數的集合。|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|在 <xref:System.Activities.Statements.FlowNode> 開始時執行的 <xref:System.Activities.Statements.Flowchart>。|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|包含 <xref:System.Activities.Statements.FlowNode> 中 <xref:System.Activities.Statements.Flowchart> 物件的集合。|

## <a name="see-also"></a>請參閱

- [流程圖](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
