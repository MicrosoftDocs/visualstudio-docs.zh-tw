---
title: ForEach&lt;T&gt;活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943858"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt;活動設計工具
<xref:System.Activities.Statements.ForEach%601> 活動會針對指定 <xref:System.Activities.Statements.ForEach%601.Body%2A> 集合中的各個項目，執行其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 中包含的活動。  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach\<T > 中工作流程設計工具屬性  
 下表顯示最為實用的 <xref:System.Activities.Statements.ForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> 活動的易記名稱。 預設值是 ForEach\<Int32 >。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|要重複項目的集合。 若要設定<xref:System.Activities.Statements.ForEach%601.Values%2A>，輸入[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]中的運算式**值**方塊**ForEach\<T >** 活動設計工具上或在屬性方格中。|  
|*TypeArgument*|True|中的項目型別<xref:System.Activities.Statements.ForEach%601.Values%2A>一般參數所指定的集合*T*。根據預設， *TypeArgument*設為**Int32**。 若要變更的類型，將變更的值*TypeArgument*屬性方格中的下拉式方塊。|  
  
 根據預設，迴圈 iterator 會命名為**項目**。 您可以在 <xref:System.Activities.Statements.ForEach%601> 活動設計工具中變更 Iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ForEach%601> 活動子系中的運算式。  
  
## <a name="see-also"></a>另請參閱  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [控制流程](../workflow-designer/control-flow-activity-designers.md)