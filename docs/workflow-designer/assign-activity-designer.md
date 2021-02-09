---
title: 工作流程設計工具-指派活動設計工具
description: 瞭解如何使用「指派」活動設計工具來建立和設定「指派」活動，以及「指派」活動如何指派值給變數或引數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe6f649543cee66a1050e5724a9317b7b8806534
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888637"
---
# <a name="assign-activity-designer"></a>Assign 活動設計工具

[ **指派** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Assign> 活動。

## <a name="the-assign-activity"></a>Assign 活動

<xref:System.Activities.Statements.Assign> 活動會指派值給變數或引數。

### <a name="using-the-assign-activity-designer"></a>使用 Assign 活動設計工具

[**指派**] 活動設計 **工具** 位於 [工具箱] 的 [**基本**] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤 (也可以從 [ **View** ] 功能表選取 [**工具箱**]，或按 CTRL + ALT + X。 ) 

[ **指派** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到已放置活動的工作流程設計工具介面上，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載 [ **指派** ] 活動設計工具會建立 <xref:System.Activities.Statements.Assign> 活動，其預設的 **DisplayName** 為 [指派]。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [**指派**] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-assign-properties"></a>Assign 屬性

下表顯示 <xref:System.Activities.Statements.Assign> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.Assign> 活動的易記名稱。 預設為 Assign。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Assign.To%2A>|是|<xref:System.Activities.Statements.Assign.Value%2A> 指派至的變數或引數。 值必須是有效的 Visual Basic 識別碼。 若要設定屬性，請在 [**指派**] 活動設計工具的 [**到**] 方塊或在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.Assign.Value%2A>|是|指派給變數的值。 若要設定 <xref:System.Activities.Statements.Assign.Value%2A> ，請在 [**指派**] 活動設計工具的 [**值**] 方塊或在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱

- [基本](../workflow-designer/primitives-activity-designers.md)
- [延遲](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)