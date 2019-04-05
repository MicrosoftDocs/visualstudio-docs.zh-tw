---
title: TerminateWorkflow 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b471cee4a07722e37ae4b58817823dd4fa48ee26
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940805"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 活動設計工具
**TerminateWorkflow**活動設計工具會用來建立及設定<xref:System.Activities.Statements.TerminateWorkflow>活動。  
  
## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 活動  
 <xref:System.Activities.Statements.TerminateWorkflow> 活動會終止工作流程的執行。  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>使用 TerminateWorkflow 活動設計工具  
 **TerminateWorkflow**活動設計工具位於**執行階段**類別**工具箱**，即可存取的哪一個**工具箱**  索引標籤 (或者，選取**工具箱**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **TerminateWorkflow**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.TerminateWorkflow>活動，具有預設值**DisplayName** TerminateWorkflow。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**TerminateWorkflow**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 屬性  
 下表顯示 <xref:System.Activities.Statements.TerminateWorkflow> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 活動的易記名稱。 預設值為 TerminateWorkflow。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|當工作流程終止時所要擲回的例外狀況。 請在屬性方格中設定這個屬性。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|說明工作流程終止的原因。 請在屬性方格中設定這個屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [執行階段](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)