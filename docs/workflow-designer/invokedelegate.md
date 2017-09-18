---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# InvokeDelegate
\[**InvokeDelegate**\] 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.InvokeDelegate> 活動。  
  
## InvokeDelegate 活動  
 <xref:System.Activities.Statements.InvokeDelegate> 會呼叫公用委派。  
  
### 使用 InvokeDelegate 活動設計工具  
 \[**InvokeDelegate**\] 活動設計工具位於 \[**工具箱**\] 的 \[**基本**\] 類別中，按一下 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的 \[**工具箱**\] 索引標籤可存取此工具 \(也可以從 \[**檢視**\] 功能表選取 \[**工具箱**\]，或是按 CTRL\+ALT\+X\)。  
  
 \[**InvokeDelegate**\] 活動設計工具可以從 \[**工具箱**\] 拖曳出來，放到 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上通常用來放置活動的任一處，例如 <xref:System.Activities.Statements.Sequence> 內部。這會建立一個 <xref:System.Activities.Statements.InvokeDelegate> 活動，具有 InvokeDelegate 的預設 <xref:System.Activities.Activity.DisplayName%2A>。<xref:System.Activities.Activity.DisplayName%2A> 可以在 \[**InvokeDelegate**\] 活動設計工具的標頭中編輯，或是在屬性方格的 \[**DisplayName**\] 方塊中編輯。  
  
### InvokeDelegate 屬性  
 下表顯示 <xref:System.Activities.Statements.InvokeDelegate> 屬性，並且描述屬性在設計工具中的使用方式。這些屬性可以在屬性方格中進行編輯，其中有一些可以在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 設計工具介面上編輯。  
  
|屬性名稱|必要|使用方式|  
|----------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 活動的易記名稱。預設值為 InvokeDelegate。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|活動執行時要呼叫之 <xref:System.Activities.Statements.ActivityDelegate> 的名稱。此屬性也可以在設計工具介面上編輯。這是必要的屬性。|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|被呼叫之委派的引數集合。金鑰是 <xref:System.Activities.Statements.ActivityDelegate> 上 <xref:System.Activities.Statements.ActivityDelegateParameter> 物件的名稱，而值是評估所屬運算式並將其指派至對應 <xref:System.Activities.Statements.ActivityDelegateParameter> 物件的引數。在屬性方格中，按一下 \[**DelegateArguments**\] 欄位中的省略符號按鈕，隨即顯示可讓您設定此屬性的 \[**DelegateArguments**\] 對話方塊。按一下 \[**建立引數**\] 欄位來加入引數。|  
  
## 請參閱  
 [HOW TO：定義並取用工作流程設計工具中的活動委派](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)