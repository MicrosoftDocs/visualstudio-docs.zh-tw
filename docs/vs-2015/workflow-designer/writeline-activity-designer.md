---
title: WriteLine 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 591ecf53e04eaff115d45e1358f385a009ab29f5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940287"
---
# <a name="writeline-activity-designer"></a>WriteLine 活動設計工具
**WriteLine**活動設計工具會用來建立及設定<xref:System.Activities.Statements.WriteLine>活動。  
  
## <a name="the-writeline-activity"></a>WriteLine 活動。  
 <xref:System.Activities.Statements.WriteLine> 活動會將文字寫入至指定的 <xref:System.IO.TextWriter> 物件。 如果未指定任何 <xref:System.IO.TextWriter>，<xref:System.Activities.Statements.WriteLine> 就會將文字寫入至主控台。  
  
### <a name="using-the-writeline-activity-designer"></a>使用 WriteLine 活動設計工具  
 **WriteLine**活動設計工具可在**基本型別**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **WriteLine**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.WriteLine> 活動，具有 WriteLine 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**WriteLine**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-writeline-properties"></a>WriteLine 屬性  
 下表顯示 <xref:System.Activities.Statements.WriteLine> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> 活動的易記名稱。 預設值為 WriteLine。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|要寫入的文字。 若要設定此屬性，輸入 在 Visual Basic 運算式**文字**方塊**WriteLine**活動設計工具上或在屬性方格中。|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> 從中寫入 <xref:System.Activities.Statements.WriteLine> 的 <xref:System.Activities.Statements.WriteLine.Text%2A>。 預設值為主控台。|  
  
## <a name="see-also"></a>另請參閱  
 [基本項目](../workflow-designer/primitives-activity-designers.md)   
 [指派](../workflow-designer/assign-activity-designer.md)   
 [延遲](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)