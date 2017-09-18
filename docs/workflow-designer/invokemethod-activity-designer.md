---
title: "InvokeMethod 活動設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# InvokeMethod 活動設計工具
\[**InvokeMethod**\] 設計工具是用來建立及設定 <xref:System.Activities.Statements.InvokeMethod> 活動。  
  
## InvokeMethod 活動  
 <xref:System.Activities.Statements.InvokeMethod> 會呼叫指定物件或型別的公用方法。  
  
### 使用 InvokeMethod 活動設計工具  
 \[**InvokeMethod**\] 活動設計工具位於 \[**工具箱**\] 的 \[**基本**\] 類別中，請按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的 \[**工具箱**\] 索引標籤存取此工具 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**InvokeMethod**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.InvokeMethod> 活動，具有 InvokeMethod 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**InvokeMethod**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### InvokeMethod 屬性  
 下表顯示 <xref:System.Activities.Statements.InvokeMethod> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 活動的易記名稱。預設值為 InvokeMethod。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|活動執行時要呼叫之方法的名稱。所呼叫的方法必須宣告為 **public**。此屬性也可以在設計工具介面上編輯。這是必要的屬性。|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|要呼叫之方法的參數集合。將參數加入集合時，順序必須與參數出現在方法簽章中的順序相同。在屬性方格中，按一下 \[**參數**\] 欄位的橢圓形按鈕，隨即顯示讓您設定此屬性的 \[**參數**\] 對話方塊。按一下 \[**建立引數**\] 按鈕來加入參數。|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|方法呼叫的傳回值。|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|指定是否要非同步呼叫方法。預設值為 **False**。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|包含要呼叫之方法的物件。此屬性也可以在設計工具介面上編輯。<br /><br /> 必須設定 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 或 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>。|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 的型別。此屬性也可以在設計工具介面上編輯。呼叫的方法必須是靜態的，才能設定此屬性。|  
  
 若要傳遞參數為 C\# **out** 參數 \(例如，`Method1(out myParam)),`\)，您應使用 **OutArgument** 而非 **InOutArgument**  
  
 無法使用 <xref:System.Activities.Statements.InvokeMethod> 活動來叫用包含稱為 **TargetObject** 或 **Result** 之引數的方法。這是因為 <xref:System.Activities.Statements.InvokeMethod> 活動會在 <xref:System.Activities.Activity.CacheMetadata%2A> 中登錄 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>、<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 和 <xref:System.Activities.Statements.InvokeMethod.Result%2A>。  
  
 以下清單顯示在 <xref:System.Activities.Activity.CacheMetadata%2A> 中登錄參數的演算法：  
  
1.  登錄 <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 引數。  
  
2.  登錄 <xref:System.Activities.Statements.InvokeMethod.Result%2A> 引數。  
  
3.  逐一查看 <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 集合並登錄每個引數。  
  
 結果的例外狀況是包含以下訊息的 <xref:System.Activities.InvalidWorkflowException> 類型：'InvokeMethod'：已有名稱為 'TargetObject' 的變數、RuntimeArgument 或 DelegateArgument。名稱在環境範圍中必須是唯一的。  
  
 這個限制不適用於 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 和 <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>，因為它們並非工作流程引數，因此並未登錄於 <xref:System.Activities.Activity.CacheMetadata%2A> 方法中 <xref:System.Activities.Statements.InvokeMethod> 活動的 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 集合。  
  
## 請參閱  
 [基本](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)