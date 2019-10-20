---
title: 工作流程設計工具 While 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6570a80de5be17b2893fc4105f057e655e841881
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649771"
---
# <a name="while-activity-designer"></a>While 活動設計工具

@No__t_0 活動會執行其 <xref:System.Activities.Statements.While.Body%2A> 中包含的活動，而指定的 <xref:System.Activities.Statements.While.Condition%2A> 則評估為**true**。 包含的活動可能永遠不會執行。 如果您要包含的活動至少執行一次，請改用 <xref:System.Activities.Statements.DoWhile> 活動。

## <a name="while-properties-in-workflow-designer"></a>工作流程設計工具中的 While 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.While> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活動設計工具在標頭中的易記名稱。 預設值為 While。 此值可以在 [**屬性**] 視窗中編輯，或直接在活動設計工具標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.While.Body%2A>|False|包含 <xref:System.Activities.Statements.While.Condition%2A> 評估為**true**時要執行的活動。|
|<xref:System.Activities.Statements.While.Condition%2A>|True|包含評估的 Visual Basic 運算式，用來判斷是否要執行 <xref:System.Activities.Statements.While.Body%2A> 中的活動。|

## <a name="see-also"></a>請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)