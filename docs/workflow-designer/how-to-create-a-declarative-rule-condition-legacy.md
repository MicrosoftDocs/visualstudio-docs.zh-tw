---
title: "HOW TO：建立宣告式規則條件 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "條件陳述式, 宣告式規則條件"
  - "宣告式規則條件"
  - "規則條件編輯器對話方塊"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# HOW TO：建立宣告式規則條件 (舊版)
本主題描述當使用以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標的舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 時，如何宣告規則條件。  
  
 條件陳述式會評估為 **True** 或 **False**。宣告式規則條件是一種使用[規則條件編輯器對話方塊 \(舊版\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)建立的條件陳述式，以 XML 格式與工作流程一起儲存。它可以包括述詞 \(Predicate\)，這些述詞會比較工作流程狀態和結合多個述詞的布林值代數。  
  
 宣告式規則條件用於以下的 Windows Workflow Foundation 全新活動中：  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### 若要使用規則條件編輯器建立宣告式規則條件  
  
1.  在活動的 \[**屬性**\] 視窗中，視活動不同選擇按一下 \[**Condition**\] 屬性或 \[**UntilCondition**\] 屬性。  
  
2.  選取屬性清單中的 \[**宣告式規則條件**\]。  
  
3.  展開 \[**Condition**\] 或 \[**UntilCondition**\] 屬性。  
  
4.  按一下 \[**ConditionName**\] 屬性。  
  
5.  按一下 \[**ConditionName**\] 省略符號 **\[…\]**，以開啟 \[**選取條件**\] 對話方塊。  
  
6.  按一下 \[**新增條件**\] 開啟 \[**規則條件編輯器**\] 對話方塊。  
  
7.  在 \[**條件**\] 文字方塊中，輸入條件運算式。  
  
     如需如何建立條件運算式的詳細資訊，請參閱[規則條件編輯器對話方塊 \(舊版\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)。  
  
8.  建立條件運算式完成後，按一下 \[**確定**\] 關閉對話方塊，則會以指定的名稱建立規則條件。  
  
     \[**選取條件**\] 對話方塊隨即開啟。  
  
     如需如何使用 \[**選取條件**\] 對話方塊的詳細資訊，請參閱[選取條件對話方塊 \(舊版\)](../workflow-designer/select-condition-dialog-box-legacy.md)。  
  
## 請參閱  
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [使用 ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [使用 IfElseBranchActivity 活動](http://go.microsoft.com/fwlink?LinkID=65075)   
 [使用 Replicator 活動](http://go.microsoft.com/fwlink?LinkID=65080)   
 [使用 While 活動](http://go.microsoft.com/fwlink?LinkID=65091)   
 [規則條件編輯器對話方塊 \(舊版\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [選取條件對話方塊 \(舊版\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [在工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)