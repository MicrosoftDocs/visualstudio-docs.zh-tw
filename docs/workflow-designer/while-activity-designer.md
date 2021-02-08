---
title: 工作流程設計工具 While 活動設計工具
description: 瞭解 While 活動在指定的條件評估為 true 時，如何執行其主體中包含的活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837992"
---
# <a name="while-activity-designer"></a>While 活動設計工具

<xref:System.Activities.Statements.While>活動會執行其包含的活動， <xref:System.Activities.Statements.While.Body%2A> 而指定的 <xref:System.Activities.Statements.While.Condition%2A> 評估結果為 **true**。 包含的活動可能永遠不會執行。 如果您要包含的活動至少執行一次，請改用 <xref:System.Activities.Statements.DoWhile> 活動。

## <a name="while-properties-in-workflow-designer"></a>工作流程設計工具中的 While 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.While> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.While> 活動設計工具在標頭中的易記名稱。 預設值為 While。 值可以在 [ **屬性** ] 視窗中編輯，或直接在活動設計工具標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.While.Body%2A>|否|包含 <xref:System.Activities.Statements.While.Condition%2A> 評估為 **true** 時所要執行的活動。|
|<xref:System.Activities.Statements.While.Condition%2A>|是|包含評估的 Visual Basic 運算式，以判斷是否要執行中的活動 <xref:System.Activities.Statements.While.Body%2A> 。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
