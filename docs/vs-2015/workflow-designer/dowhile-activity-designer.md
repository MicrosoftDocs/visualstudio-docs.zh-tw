---
title: DoWhile 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09954409baccfdc5d9eb083a15bd02f5d16cb85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941214"
---
# <a name="dowhile-activity-designer"></a>DoWhile 活動設計工具
<xref:System.Activities.Statements.DoWhile>活動會在執行中包含的活動及其<xref:System.Activities.Statements.DoWhile.Body%2A>至少一次，直到指定的條件評估為為止**false**。 如果您需要包含在迴圈主體中的活動執行零次或多次，請改用 <xref:System.Activities.Statements.While> 活動。  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>工作流程設計工具中的 DoWhile 屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.DoWhile> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|要執行的條件時的活動 **，則為 true**。 若要新增<xref:System.Activities.Statements.DoWhile.Body%2A>活動，請從工具箱拖曳到**主體**方塊**DoWhile**活動設計工具提示文字 「 置放活動 」 與。|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|在每次迴圈重複之後所要評估的條件。 若要設定<xref:System.Activities.Statements.DoWhile.Condition%2A>，輸入[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]中的運算式**條件**方塊**DoWhile**活動設計工具上或在屬性方格中。|  
  
## <a name="see-also"></a>另請參閱  
 [時](../workflow-designer/while-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)