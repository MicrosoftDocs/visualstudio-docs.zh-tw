---
title: 如何： 建立宣告式規則條件 （舊版） |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2508404840db81f03ba4865a3e5d5af91e5c653b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187404"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>HOW TO：建立宣告式規則條件 (舊版)
本主題描述當使用以 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標的舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 時，如何宣告規則條件。  
  
 條件陳述式評估為**真**或是**False**。 宣告式規則條件會使用建立的條件陳述式[規則條件編輯器對話方塊 （舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)和與工作流程儲存為 XML。 它可以包括述詞 (Predicate)，這些述詞會比較工作流程狀態和結合多個述詞的布林值代數。  
  
 宣告式規則條件用於以下的 Windows Workflow Foundation 全新活動中：  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>若要使用規則條件編輯器建立宣告式規則條件  
  
1.  在活動的**屬性** 視窗中，按一下**條件**屬性或**UntilCondition**屬性，視活動而定。  
  
2.  選取 **宣告式規則條件**從屬性清單。  
  
3.  依序展開**條件**或是**UntilCondition**屬性。  
  
4.  按一下  **ConditionName**屬性。  
  
5.  按一下 [ **ConditionName**省略符號 **[...]** 以開啟**選取條件**] 對話方塊。  
  
6.  按一下 [**新的條件**來開啟**規則條件編輯器**] 對話方塊。  
  
7.  輸入中的條件運算式**條件**文字方塊。  
  
     如需有關如何建立條件運算式的資訊，請參閱 <<c0> [ 規則條件編輯器對話方塊 （舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)。  
  
8.  當您完成建立條件運算式時，按一下**確定**關閉對話方塊，並使用指派的名稱建立的規則條件。  
  
     **選取條件**對話方塊隨即開啟。  
  
     如需有關如何使用資訊**選取條件** 對話方塊中，請參閱[選取條件對話方塊 （舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)。  
  
## <a name="see-also"></a>另請參閱  
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)   
 [使用 ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [使用 IfElseBranchActivity 活動](http://go.microsoft.com/fwlink?LinkID=65075)   
 [使用 Replicator 活動](http://go.microsoft.com/fwlink?LinkID=65080)   
 [使用 While 活動](http://go.microsoft.com/fwlink?LinkID=65091)   
 [規則條件編輯器對話方塊 （舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [選取條件對話方塊 （舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)