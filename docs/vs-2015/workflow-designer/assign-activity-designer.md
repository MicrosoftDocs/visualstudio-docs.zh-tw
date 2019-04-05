---
title: Assign 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 111f53ec5b427207a6bde5d590cf8f1c908ff130
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940538"
---
# <a name="assign-activity-designer"></a>Assign 活動設計工具
**指派**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Assign>活動。  
  
## <a name="the-assign-activity"></a>Assign 活動  
 <xref:System.Activities.Statements.Assign> 活動會指派值給變數或引數。  
  
### <a name="using-the-assign-activity-designer"></a>使用 Assign 活動設計工具  
 **指派**活動設計工具可在**基本型別**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤 (或者，選取**工具箱**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **指派**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Assign>活動，具有預設值**DisplayName**的指派。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**指派**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-assign-properties"></a>Assign 屬性  
 下表顯示 <xref:System.Activities.Statements.Assign> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> 活動的易記名稱。 預設為 Assign。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|<xref:System.Activities.Statements.Assign.Value%2A> 指派至的變數或引數。 這必須是有效的 Visual Basic 識別項。 若要設定此屬性，輸入 在 Visual Basic 運算式**要**方塊**指派**活動設計工具上或在屬性方格中。|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|指派給變數的值。 若要設定<xref:System.Activities.Statements.Assign.Value%2A>，輸入在 Visual Basic 運算式**值**方塊**指派**活動設計工具上或在屬性方格中。|  
  
## <a name="see-also"></a>另請參閱  
 [基本項目](../workflow-designer/primitives-activity-designers.md)   
 [延遲](../workflow-designer/delay-activity-designer.md)   
 [叫用方法](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)