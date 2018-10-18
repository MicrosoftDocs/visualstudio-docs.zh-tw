---
title: 序列活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d676c4270d636d0869d5b2f95f7a265bf0a085ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282772"
---
# <a name="sequence-activity-designer"></a>Sequence 活動設計工具
<xref:System.Activities.Statements.Sequence> 活動會包含子活動的已排序集合，而該集合會依序執行。  
  
 另一種依序執行一組活動的方式，則是使用 <xref:System.Activities.Statements.Flowchart> 活動。 請考慮使用[流程圖](../workflow-designer/flowchart-activity-designer.md)當您有一個簡單的分支或迴圈執行的程式，您想要用圖表表示模型。  
  
## <a name="using-the-sequence-activity-designer"></a>使用 Sequence 活動設計工具  
 新增<xref:System.Activities.Statements.Sequence>活動，拖曳**順序**活動設計工具，從**工具箱**拖放入[!INCLUDE[wfd1](../includes/wfd1-md.md)]介面。 若要將子活動新增至這<xref:System.Activities.Statements.Sequence>活動，從一些其他活動拖曳到**工具箱**拖放上提示文字的方塊中的三角形 」 在此放置活動 」。  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Sequence 活動屬性  
 下表顯示 <xref:System.Activities.Statements.Sequence> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Sequence> 活動設計工具在標頭中的易記名稱。 預設值為 Sequence。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
  
## <a name="see-also"></a>另請參閱  
 [流程圖](../workflow-designer/flowchart-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)