---
title: "延遲活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 24ca658650c3b0eeb28261753b06082214cdb838
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="delay-activity-designer"></a>Delay 活動設計工具
**延遲**活動設計工具用來建立及設定<xref:System.Activities.Statements.Delay>活動。  
  
## <a name="the-delay-activity"></a>Delay 活動  
 <xref:System.Activities.Statements.Delay> 活動會延遲某個工作流程的執行，等候指定的時間長度。  
  
### <a name="using-the-delay-activity-designer"></a>使用 Delay 活動設計工具  
 **延遲**活動設計工具位於**基本型別**分類**工具箱**，即可存取的哪一個**工具箱** 索引標籤[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **延遲**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.Delay> 活動，具有 Delay 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可編輯的標頭中**延遲**活動設計工具或在**DisplayName**屬性方格的方塊。  
  
### <a name="the-delay-properties"></a>Delay 屬性  
 下表顯示 <xref:System.Activities.Statements.Delay> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> 活動的易記名稱。 預設為 Delay。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|延遲工作流程的時間長度。 這個屬性會在屬性方格中設定。 輸入常值 <xref:System.TimeSpan> (使用 00:00:00 格式) 或 Visual Basic 運算式，即可指定時間長度。|  
  
## <a name="see-also"></a>請參閱  
 [基本類型](../workflow-designer/primitives-activity-designers.md)   
 [指派](../workflow-designer/assign-activity-designer.md)   
 [Delay 活動設計工具](../workflow-designer/delay-activity-designer.md)   
 [叫用方法](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)