---
title: "如何： 建立 PolicyActivity 規則集 （舊版） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 49c511c2d881a9996efe07dcc030e80e21a8cf88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>HOW TO：建立 PolicyActivity 規則集 (舊版)
本主題描述當使用以 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 為目標的舊版 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 時，如何建立原則活動規則集。  
  
 您拖曳之後**原則**活動項目從**工具箱**至工作流程設計介面中，您會想要選取現有的規則或建立新的規則集[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)活動。 選取現有的規則設定使用[選取規則集對話方塊 （舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)和使用建立規則集[規則集編輯器對話方塊 （舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)。  
  
> [!NOTE]
>  您可以開啟[規則集編輯器對話方塊 （舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)對話方塊直接按兩下[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)工作流程設計介面上的活動。  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>若要選取或建立 PolicyActivity 活動的規則集  
  
1.  以滑鼠右鍵按一下[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)，然後按一下 **屬性**開啟**屬性**視窗。  
  
2.  按一下**RuleSetReference**屬性。  
  
3.  執行下列任一步驟：  
  
    -   按一下**RuleSetReference**省略**[…]**，然後選取 現有的規則集[選取規則集對話方塊 （舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)。 接著移至步驟 10。  
  
         -或-  
  
    -   輸入規則集的名稱。 按一下**RuleSetReference**省略**[…]**，然後選取**編輯**中[選取規則集對話方塊 （舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)。  
  
         -或-  
  
    -   輸入規則集的名稱。 展開**RuleSetReference**屬性，並選取省略符號**[…]**中**RuleSet Definition**屬性。  
  
         [規則集編輯器對話方塊 （舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)隨即開啟。  
  
4.  在[規則集編輯器對話方塊 （舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)，按一下 **加入規則**將新的規則新增至規則集。  
  
5.  輸入**名稱**，**優先順序**，和**重新評估**屬性，或保留預設值。  
  
6.  輸入的文字**條件**。  
  
7.  輸入的文字**Then 動作**和**Else 動作**。  
  
8.  按一下**加入規則**再次加入另一項規則。  
  
9. 完成後，請按一下 [確定] 。  
  
## <a name="see-also"></a>另請參閱  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [選取規則集對話方塊 （舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [規則集編輯器對話方塊 （舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [使用 [原則] 活動](http://go.microsoft.com/fwlink?LinkID=65004)   
 [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)