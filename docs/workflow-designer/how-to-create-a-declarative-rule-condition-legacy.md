---
title: 工作流程設計工具-如何： 建立宣告式規則條件 （舊版）
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43b359040256788db240274f43f706b41f01d021
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>HOW TO：建立宣告式規則條件 (舊版)

本主題描述如何宣告規則條件使用舊版的 Windows 工作流程設計工具的目標為.NET Framework 3.5 版或 WinFX。

條件陳述式會評估為**True**或**False**。 宣告式規則條件是條件陳述式所建立的使用[規則條件編輯器對話方塊 （舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)並以 XML 格式儲存與工作流程。 它可以包括述詞 (Predicate)，這些述詞會比較工作流程狀態和結合多個述詞的布林值代數。

宣告式規則條件用於以下的 Windows Workflow Foundation 全新活動中：

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

## <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>若要使用規則條件編輯器建立宣告式規則條件

1.  在活動中**屬性**視窗中，按一下 **條件**屬性或**UntilCondition**屬性，根據活動。

2.  選取**宣告式規則條件**從屬性清單。

3.  展開**條件**或**UntilCondition**屬性。

4.  按一下**ConditionName**屬性。

5.  按一下**ConditionName**省略 **[…]** 開啟**選取條件** 對話方塊。

6.  按一下**新條件**開啟**規則條件編輯器** 對話方塊。

7.  輸入的運算式中的條件**條件**文字方塊。

     如需如何建立條件運算式的資訊，請參閱[規則條件編輯器對話方塊 （舊版）](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)。

8.  當您完成建立條件運算式，請按一下**確定**關閉對話方塊並建立規則條件，以指定的名稱。

     **選取條件**對話方塊隨即開啟。

     如需有關如何使用資訊**選取條件**對話方塊中，請參閱[選取條件對話方塊 （舊版）](../workflow-designer/select-condition-dialog-box-legacy.md)。

## <a name="see-also"></a>另請參閱

- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)
- [使用 ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)
- [使用 IfElseBranchActivity 活動](http://go.microsoft.com/fwlink?LinkID=65075)
- [使用複寫器活動](http://go.microsoft.com/fwlink?LinkID=65080)
- [使用 While 活動](http://go.microsoft.com/fwlink?LinkID=65091)
- [規則條件編輯器對話方塊 (舊版)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [選取條件對話方塊 (舊版)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [在工作流程中使用條件](http://go.microsoft.com/fwlink?LinkID=65009)