---
title: 如何：建立 (舊版) 的宣告式規則條件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849328"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>HOW TO：建立宣告式規則條件 (舊版)
本主題描述當使用以 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標的舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 時，如何宣告規則條件。

 條件陳述式的評估結果為 **True** 或 **False**。 宣告式規則條件是使用 [ [規則條件編輯器] 對話方塊 ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) 所建立的條件陳述式 (舊版) 並以 XML 形式儲存在工作流程中。 它可以包括述詞 (Predicate)，這些述詞會比較工作流程狀態和結合多個述詞的布林值代數。

 宣告式規則條件用於以下的 Windows Workflow Foundation 全新活動中：

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>若要使用規則條件編輯器建立宣告式規則條件

1. 在活動的 [ **屬性** ] 視窗中，按一下 [ **條件** ] 屬性或 [ **UntilCondition** ] 屬性（視活動而定）。

2. 從屬性清單中選取 [ **宣告式規則條件** ]。

3. 展開 [ **條件** ] 或 [ **UntilCondition** ] 屬性。

4. 按一下 [ **conditionname]** ] 屬性。

5. 按一下 [ **conditionname]** **] 省略號 [...]** 以開啟 [ **選取條件** ] 對話方塊。

6. 按一下 [ **新增條件** ] 以開啟 [ **規則條件編輯器** ] 對話方塊。

7. 在 [ **條件** ] 文字方塊中，輸入條件的運算式。

     如需有關如何建立條件運算式的詳細資訊，請參閱 [ (舊版) 的 [規則條件編輯器] 對話方塊 ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)。

8. 當您完成建立條件運算式時，請按一下 **[確定** ] 關閉對話方塊，並建立具有指派名稱的規則條件。

     [ **選取條件** ] 對話方塊隨即開啟。

     如需有關如何使用 [ **選取條件** ] 對話方塊的詳細資訊，請參閱 [ (舊版) 的 [選取條件] 對話方塊 ](../workflow-designer/select-condition-dialog-box-legacy.md)。

## <a name="see-also"></a>另請參閱
 使用[ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx)的[舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)使用[IfElseBranchActivity 活動](https://msdn2.microsoft.com/library/bb628465.aspx)，使用 [ [While 活動](https://msdn2.microsoft.com/library/bb628552.aspx)[規則條件編輯器] 對話方塊 (舊版) ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [選取 [條件] 對話方塊 (舊版) ](../workflow-designer/select-condition-dialog-box-legacy.md) [使用工作流程中](https://msdn2.microsoft.com/library/bb628447.aspx)[的](https://msdn2.microsoft.com/library/bb628544.aspx)條件
