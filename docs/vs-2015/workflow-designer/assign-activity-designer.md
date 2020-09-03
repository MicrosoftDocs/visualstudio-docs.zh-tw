---
title: 指派活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659194"
---
# <a name="assign-activity-designer"></a>Assign 活動設計工具
[ **指派** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Assign> 活動。

## <a name="the-assign-activity"></a>Assign 活動
 <xref:System.Activities.Statements.Assign> 活動會指派值給變數或引數。

### <a name="using-the-assign-activity-designer"></a>使用 Assign 活動設計工具
 [**指派**] 活動設計**工具**位於 [工具箱] 的 [**基本**] 類別中，若要存取，請按一下 [**工具箱**] 索引標籤 (也可以從 [ **View** ] 功能表選取 [**工具箱**]，或按 CTRL + ALT + X。 ) 

 [ **指派** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 放置活動的位置，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.Assign> 活動，其中包含 [指派] 的預設 **DisplayName** 。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [**指派**] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-assign-properties"></a>Assign 屬性
 下表顯示 <xref:System.Activities.Statements.Assign> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.Assign> 活動的易記名稱。 預設為 Assign。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.Assign.To%2A>|是|<xref:System.Activities.Statements.Assign.Value%2A> 指派至的變數或引數。 這必須是有效的 Visual Basic 識別項。 若要設定屬性，請在 [**指派**] 活動設計工具的 [**到**] 方塊或在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.Assign.Value%2A>|是|指派給變數的值。 若要設定 <xref:System.Activities.Statements.Assign.Value%2A> ，請在 [**指派**] 活動設計工具的 [**值**] 方塊或在屬性方格中輸入 Visual Basic 運算式。|

## <a name="see-also"></a>另請參閱
 [基本](../workflow-designer/primitives-activity-designers.md)[延遲](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)