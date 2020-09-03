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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606614"
---
# <a name="while-activity-designer"></a>While 活動設計工具

<xref:System.Activities.Statements.While>活動會執行其包含的活動， <xref:System.Activities.Statements.While.Body%2A> 而指定的條件評估為**true**。 包含的活動可能永遠不會執行。 如果您要包含的活動至少執行一次，請改用 <xref:System.Activities.Statements.DoWhile> 活動。

## <a name="while-properties-in-workflow-designer"></a>工作流程設計工具中的 While 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.While> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.While> 活動設計工具在標頭中的易記名稱。 預設值為 While。 值可以在 [ **屬性** ] 視窗中編輯，或直接在活動設計工具標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.While.Body%2A>|否|包含 <xref:System.Activities.Statements.While.Condition%2A> 評估為 **true**時所要執行的活動。|
|<xref:System.Activities.Statements.While.Condition%2A>|是|包含要評估的 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 運算式，用於判斷是否要執行 <xref:System.Activities.Statements.While.Body%2A> 中的活動。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)