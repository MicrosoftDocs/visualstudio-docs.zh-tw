---
title: 如何：建立 PolicyActivity 規則集（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849322"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>HOW TO：建立 PolicyActivity 規則集 (舊版)
本主題描述當使用以 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標的舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 時，如何建立原則活動規則集。

 當您從 [**工具箱**] 將 [**原則**] 活動專案拖曳至工作流程設計介面之後，您會想要選取現有的規則，或為[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)活動建立新的規則集。 您可以使用 [[選取規則集] 對話方塊（舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)來選取現有的規則集，並使用 [[規則集編輯器] 對話方塊（舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)來建立規則集。

> [!NOTE]
> 您可以按兩下工作流程設計介面上的[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)活動，直接開啟 [[規則集編輯器] 對話方塊（舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)對話方塊。

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>若要選取或建立 PolicyActivity 活動的規則集

1. 以滑鼠右鍵按一下[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)，然後按一下 [**屬性**] 以開啟 [**屬性**] 視窗。

2. 按一下  **rulesetreference**  屬性。

3. 請執行下列其中一項動作：

    - 按一下 [ **rulesetreference**省略號 **[...]]** ，然後在 [選取規則集 對話方塊](../workflow-designer/select-rule-set-dialog-box-legacy.md)中選取現有的規則集（舊版）。 接著移至步驟 10。

         -或-

    - 輸入規則集的名稱。 按一下 [ **rulesetreference**省略號 **[...]]** ，然後選取 [[選取規則集] 對話方塊（舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md)中的 [**編輯**]。

         -或-

    - 輸入規則集的名稱。 展開 [ **rulesetreference** ] 屬性，然後選取 [**規則集定義**] 屬性中的省略號 **[...]** 。

         [[規則集編輯器] 對話方塊（舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)隨即開啟。

4. 在 [[規則集編輯器] 對話方塊（舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)中，按一下 [新增**規則**]，將新規則新增至規則集。

5. 輸入 [**名稱**]、[**優先順序**] 和 [重新**評估**] 屬性，或保留預設值。

6. 輸入**條件**的文字。

7. 輸入 [ **Then 動作**] 和 [ **Else 動作**] 的文字。

8. 再次按一下 [**新增規則**] 以新增另一個規則。

9. 完成後，請按一下 [確定]。

## <a name="see-also"></a>請參閱
 [使用原則活動](https://msdn2.microsoft.com/library/bb675229.aspx)[舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)的[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [選取規則集對話方塊（舊版）](../workflow-designer/select-rule-set-dialog-box-legacy.md) [規則集編輯器對話方塊（舊版）](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
