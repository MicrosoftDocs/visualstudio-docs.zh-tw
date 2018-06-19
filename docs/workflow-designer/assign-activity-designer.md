---
title: 工作流程設計工具-Assign 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44d825d5d6ee36876c807ce067c71c1b10896623
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971422"
---
# <a name="assign-activity-designer"></a>Assign 活動設計工具

**指派**活動設計工具用來建立及設定<xref:System.Activities.Statements.Assign>活動。

## <a name="the-assign-activity"></a>Assign 活動

<xref:System.Activities.Statements.Assign> 活動會指派值給變數或引數。

### <a name="using-the-assign-activity-designer"></a>使用 Assign 活動設計工具

**指派**活動設計工具位於**基本型別**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤 (或者，選取**工具箱**從**檢視**功能表或 CTRL + ALT + X。)

**指派**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，因為在放置活動的例如內部<xref:System.Activities.Statements.Sequence>。 卸除**指派**活動設計工具建立<xref:System.Activities.Statements.Assign>預設值的活動**DisplayName**的指派。 <xref:System.Activities.Activity.DisplayName%2A>可編輯的標頭中**指派**活動設計工具或在**DisplayName**屬性方格的方塊。

### <a name="the-assign-properties"></a>Assign 屬性

下表顯示 <xref:System.Activities.Statements.Assign> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中編輯，其中部分可以在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> 活動的易記名稱。 預設為 Assign。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Assign.To%2A>|True|<xref:System.Activities.Statements.Assign.Value%2A> 指派至的變數或引數。 值必須是有效的 Visual Basic 識別項。 若要設定此屬性，輸入 Visual Basic 運算式**至**方塊**指派**活動設計工具，或在屬性方格中。|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|指派給變數的值。 若要設定<xref:System.Activities.Statements.Assign.Value%2A>，輸入在 Visual Basic 運算式**值**方塊**指派**活動設計工具，或在屬性方格中。|

## <a name="see-also"></a>另請參閱

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [延遲](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)