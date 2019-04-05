---
title: InvokeMethod 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 61398efe1849c6038e13a68ae3b2e2f5f80f1d5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943108"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 活動設計工具
**InvokeMethod**設計工具會用來建立及設定<xref:System.Activities.Statements.InvokeMethod>活動。  
  
## <a name="the-invokemethod-activity"></a>InvokeMethod 活動  
 <xref:System.Activities.Statements.InvokeMethod> 會呼叫指定物件或型別的公用方法。  
  
### <a name="using-the-invokemethod-activity-designer"></a>使用 InvokeMethod 活動設計工具  
 **InvokeMethod**活動設計工具可在**基本型別**類別**工具箱**，即可存取的哪一個**工具箱**  索引標籤[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CRTL + ALT + X。)  
  
 **InvokeMethod**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.InvokeMethod> 活動，具有 InvokeMethod 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以的標頭中編輯**InvokeMethod**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-invokemethod-properties"></a>InvokeMethod 屬性  
 下表顯示 <xref:System.Activities.Statements.InvokeMethod> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 活動的易記名稱。 預設值為 InvokeMethod。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|活動執行時要呼叫之方法的名稱。 呼叫的方法必須宣告為**公開**。 此屬性也可以在設計工具介面上編輯。 這是必要的屬性。|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|要呼叫之方法的參數集合。 將參數加入至集合時，加入順序必須與參數出現在方法簽章中的順序相同。 在屬性方格中，按一下省略符號按鈕，在**參數**欄位，它會顯示**參數**對話方塊，供您設定此屬性。 按一下 **建立引數**按鈕以新增參數。|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|方法呼叫的傳回值。|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|指定是否要非同步呼叫方法。 預設值是 **False**。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|包含要呼叫之方法的物件。 此屬性也可以在設計工具介面上編輯。<br /><br /> 必須設定 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 或 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 的類型。 此屬性也可以在設計工具介面上編輯。 呼叫的方法必須是靜態的，才能設定此屬性。|  
  
 若要將參數傳遞為 C#**放大**參數 (例如`Method1(out myParam)),`應該使用**OutArgument**而不是**InOutArgument**  
  
 方法呼叫的引數**TargetObject**或是**結果**無法使用叫用<xref:System.Activities.Statements.InvokeMethod>活動。 這是因為 <xref:System.Activities.Statements.InvokeMethod> 活動會在 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 中登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>、<xref:System.Activities.Statements.InvokeMethod.Result%2A> 和 <xref:System.Activities.Activity.CacheMetadata%2A>。  
  
 以下清單顯示在 <xref:System.Activities.Activity.CacheMetadata%2A> 中登錄參數的演算法：  
  
1. 登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引數。  
  
2. 登錄 <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引數。  
  
3. 逐一查看 <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 集合並登錄每個引數。  
  
   產生的例外狀況是型別<xref:System.Activities.InvalidWorkflowException>並出現下列訊息：' InvokeMethod':變數、 RuntimeArgument 或 DelegateArgument 已經存在名稱為 'TargetObject'。 名稱在環境範圍中必須是唯一的。  
  
   這個限制不適用於 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 和 <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>，因為它們並非工作流程引數，因此並未登錄於 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 方法中 <xref:System.Activities.Statements.InvokeMethod> 活動的 <xref:System.Activities.Activity.CacheMetadata%2A> 集合。  
  
## <a name="see-also"></a>另請參閱  
 [基本項目](../workflow-designer/primitives-activity-designers.md)   
 [指派](../workflow-designer/assign-activity-designer.md)   
 [延遲](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)