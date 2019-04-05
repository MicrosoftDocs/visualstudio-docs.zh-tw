---
title: Persist 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f87997178f98e9e632b756b5a4440c19544b5c86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942563"
---
# <a name="persist-activity-designer"></a>Persist 活動設計工具
**Persist**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Persist>活動。  
  
## <a name="the-persist-activity"></a>Persist 活動  
 只要情況允許，<xref:System.Activities.Statements.Persist> 活動會將工作流程儲存至磁碟。 <xref:System.Activities.Statements.Persist> 活動無法在非持續性的區域中執行，例如在 <xref:System.Activities.Statements.TransactionScope> 活動內。 如果在非持續性的範圍內使用 <xref:System.Activities.Statements.Persist> 活動，就會在執行階段擲回例外狀況。  
  
### <a name="using-the-persist-activity-designer"></a>使用 Persist 活動設計工具  
 **Persist**活動設計工具可在**執行階段**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤 (或者，選取**工具箱**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **Persist**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立<xref:System.Activities.Statements.Persist>活動，具有預設值**DisplayName**的持續性。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**Persist**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-persist-properties"></a>Persist 屬性  
 下表顯示 <xref:System.Activities.Statements.Persist> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 活動的易記名稱。 預設為 Persist。 雖然顯示名稱並非絕對必要，但建議您盡量使用顯示名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [執行階段](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)