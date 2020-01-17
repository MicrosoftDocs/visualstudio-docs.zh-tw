---
title: 工作流程設計工具 While 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115175"
---
# <a name="while-activity-designer"></a>While 活動設計工具

<xref:System.Activities.Statements.While> 活動會執行其 <xref:System.Activities.Statements.While.Body%2A> 中包含的活動，而指定的 <xref:System.Activities.Statements.While.Condition%2A> 則評估為**true**。 包含的活動可能永遠不會執行。 如果您要包含的活動至少執行一次，請改用 <xref:System.Activities.Statements.DoWhile> 活動。

## <a name="while-properties-in-workflow-designer"></a>工作流程設計工具中的 While 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.While> 活動屬性，並且說明它們在設計工具中的使用方式。

|內容名稱|必要|使用|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活動設計工具在標頭中的易記名稱。 預設值為 While。 此值可以在 [**屬性**] 視窗中編輯，或直接在活動設計工具標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.While.Body%2A>|False|包含 <xref:System.Activities.Statements.While.Condition%2A> 評估為**true**時要執行的活動。|
|<xref:System.Activities.Statements.While.Condition%2A>|True|包含評估的 Visual Basic 運算式，用來判斷是否要執行 <xref:System.Activities.Statements.While.Body%2A> 中的活動。|

## <a name="see-also"></a>請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
