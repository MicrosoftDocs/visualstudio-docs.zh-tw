---
title: "HOW TO：建立 PolicyActivity 規則集 (舊版) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity 活動, 建立規則集"
  - "PolicyActivity 活動, 選取規則集"
  - "規則集編輯器對話方塊"
  - "規則集, 為 PolicyActivity 建立"
  - "選取規則集對話方塊"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# HOW TO：建立 PolicyActivity 規則集 (舊版)
本主題描述當使用以 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 為目標的舊版 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 時，如何建立原則活動規則集。  
  
 將 \[**工具箱**\] 中的 \[**原則**\] 活動項目拖曳至工作流程設計介面後，您可針對 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) 活動選取現有的規則或建立新的規則集。您可以使用 [選取規則集對話方塊 \(舊版\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) 選取現有規則集，或使用 [規則集編輯器對話方塊 \(舊版\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) 建立規則集。  
  
> [!NOTE]
>  您可以在工作流程設計介面上按兩下 [PolicyActivity 類別](http://go.microsoft.com/fwlink?LinkID=65019) \(英文\) 活動，直接開啟[規則集編輯器對話方塊 \(舊版\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)對話方塊。  
  
### 若要選取或建立 PolicyActivity 活動的規則集  
  
1.  以滑鼠右鍵按一下 [PolicyActivity 類別](http://go.microsoft.com/fwlink?LinkID=65019) \(英文\)，然後按一下 \[**屬性**\] 開啟 \[**屬性**\] 視窗。  
  
2.  按一下 \[**RuleSetReference**\] 屬性。  
  
3.  執行下列任一步驟：  
  
    -   按一下 \[**RuleSetReference**\] 省略符號 **\[…\]**，再選取[選取規則集對話方塊 \(舊版\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)中的現有規則集。接著移至步驟 10。  
  
         \-或\-  
  
    -   輸入規則集的名稱。按一下 \[**RuleSetReference**\] 省略符號 **\[…\]**，再選取[選取規則集對話方塊 \(舊版\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)中的 \[**編輯**\]。  
  
         \-或\-  
  
    -   輸入規則集的名稱。展開 \[**RuleSetReference**\] 屬性，選取 \[**RuleSet Definition**\] 屬性中的省略符號 **\[…\]**。  
  
         [規則集編輯器對話方塊 \(舊版\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)隨即開啟。  
  
4.  在[規則集編輯器對話方塊 \(舊版\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)中，按一下 \[**新增規則**\] 加入新規則至規則集中。  
  
5.  輸入 \[**名稱**\]、\[**優先權**\] 和 \[**重新評估**\] 屬性，或保留預設值。  
  
6.  輸入 \[**條件**\] 的文字。  
  
7.  輸入 \[**Then 動作**\] 和 \[**Else 動作**\] 的文字。  
  
8.  再按一下 \[**新增規則**\] 新增其他規則。  
  
9. 完成後，請按一下 \[**確定**\]。  
  
## 請參閱  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [選取規則集對話方塊 \(舊版\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [規則集編輯器對話方塊 \(舊版\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [使用原則活動](http://go.microsoft.com/fwlink?LinkID=65004)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)