---
title: 作法：建立宣告式規則條件（舊版） |Microsoft Docs
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
ms.openlocfilehash: 2dc63fc58b22792e566df91bd86cac40e3fd2e65
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297493"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>作法：建立宣告式規則條件 (舊版)
本主題描述當使用以 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標的舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 時，如何宣告規則條件。

 條件陳述式會評估為**True**或**False**。 宣告式規則條件是使用 [[規則條件編輯器] 對話方塊（舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)建立的條件陳述式，並以 XML 的形式儲存在工作流程中。 它可以包括述詞 (Predicate)，這些述詞會比較工作流程狀態和結合多個述詞的布林值代數。

 宣告式規則條件用於以下的 Windows Workflow Foundation 全新活動中：

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>若要使用規則條件編輯器建立宣告式規則條件

1. 在活動的 **屬性** 視窗中，按一下  **Condition**  屬性或  **untilcondition**  屬性（視活動而定）。

2. 從屬性清單中選取 [**宣告式規則條件**]。

3. 展開 **條件** 或  **untilcondition**  屬性。

4. 按一下  **conditionname**  屬性。

5. 按一下 [ **conditionname**省略號 **[...]]** 以開啟 [**選取條件** 對話方塊。

6. 按一下 [**新增條件**] 以開啟 [**規則條件編輯器**] 對話方塊。

7. 在 [**條件**] 文字方塊中輸入條件的運算式。

     如需如何建立條件運算式的詳細資訊，請參閱[規則條件編輯器對話方塊（舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)。

8. 當您完成建立條件運算式時，請按一下 **[確定]** 關閉對話方塊，並使用指派的名稱來建立規則條件。

     [**選取條件**] 對話方塊隨即開啟。

     如需如何使用 [**選取條件**] 對話方塊的詳細資訊，請參閱[選取條件對話方塊（舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)。

## <a name="see-also"></a>另請參閱
 [使用ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066) [使用 IfElseBranchActivity 活動](https://go.microsoft.com/fwlink?LinkID=65075) [使用編輯器活動](https://go.microsoft.com/fwlink?LinkID=65080)的[舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md) [使用 While 活動](https://go.microsoft.com/fwlink?LinkID=65091)[規則條件編輯器對話方塊（舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [在工作流程中使用條件的](https://go.microsoft.com/fwlink?LinkID=65009) [選取條件對話方塊（舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)