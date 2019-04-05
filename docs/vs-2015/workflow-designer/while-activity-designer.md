---
title: While 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36752df3d8ffbf33b8ea95570d6a4efe8c8cd3be
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941220"
---
# <a name="while-activity-designer"></a>While 活動設計工具

<xref:System.Activities.Statements.While>活動會在執行中包含的活動及其<xref:System.Activities.Statements.While.Body%2A>而指定的條件會評估要 **，則為 true**。 包含的活動可能永遠不會執行。 如果您要包含的活動至少執行一次，請改用 <xref:System.Activities.Statements.DoWhile> 活動。

## <a name="while-properties-in-workflow-designer"></a>工作流程設計工具中的 While 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.While> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.While> 活動設計工具在標頭中的易記名稱。 預設值為 While。 值可以在中編輯**屬性**視窗或直接在活動設計工具標頭。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.While.Body%2A>|False|包含要執行的活動時<xref:System.Activities.Statements.While.Condition%2A>評估為 **，則為 true**。|
|<xref:System.Activities.Statements.While.Condition%2A>|True|包含要評估的 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 運算式，用於判斷是否要執行 <xref:System.Activities.Statements.While.Body%2A> 中的活動。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)