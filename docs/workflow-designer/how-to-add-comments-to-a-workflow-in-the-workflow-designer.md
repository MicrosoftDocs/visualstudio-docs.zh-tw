---
title: "如何： 將註解加入至工作流程設計工具中的工作流程 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: eb7825f79ee54b02d764e4ad8754ee1382b5d41f
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>HOW TO：將註解新增至工作流程設計工具中的工作流程

為了方便建立更大型、更為複雜的工作流程，[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] 讓開發人員可以在設計工具中將註釋加入到下列項目類型：

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   衍生自 <xref:System.Activities.Statements.FlowNode> 的類別

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> 註釋的內容會以純文字的格式儲存在與工作流程相關聯 XAML 檔中，並有可能被其他人讀取。 將敏感資訊輸入至註釋時要謹慎。

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>將註釋加入到設計工具中的活動

1. 在工作流程設計工具中，以滑鼠右鍵按一下工作流程設計工具，並選取的項目**註解**，**加入註解**。

1. 在提供的空間中加入註釋的文字。

   此項目顯示註釋圖示。 註釋圖示上方註解的文字。

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>在活動的設計工具中顯示註釋

1.  與活動設計工具的註釋顯示位於活動外部，按一下  **Pin**註釋裝飾項中的圖示。

   註解會顯示在活動設計工具。 在下列螢幕擷取畫面中，註釋「工作流程中的開始活動」顯示在活動的設計工具中。

   ![活動設計工具中顯示的註釋](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

1. 若要顯示註釋的活動設計工具外，將滑鼠停留在活動設計工具中的註釋區域，按一下**取消釘選**圖示

   ![活動的設計工具外部顯示註釋](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>顯示或隱藏所有註釋

1. 以滑鼠右鍵按一下具有註釋的活動。 選取**註解**，**顯示所有註釋**。

   所有註解會顯示在活動設計工具。

1. 若要顯示的活動設計工具以外的所有註解，以滑鼠右鍵按一下活動，然後選取**註解**，**隱藏所有註解**。

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>編輯或刪除活動的註釋

1. 以滑鼠右鍵按一下具有註釋的活動。

1. 選取**註解**，**編輯註釋**或**刪除註釋**。

   開啟要編輯或刪除註解。

1. 若要同時刪除所有註解，請以滑鼠右鍵按一下工作流程設計工具，並選取**註解**，**刪除所有註解**。

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>加入、編輯和刪除變數或引數的註釋

1. 以滑鼠右鍵按一下變數或引數，並選取 [新增註釋]。

1. 輸入註釋的文字。 變數或引數會顯示註釋圖示。

1. 以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [編輯註釋]。

   註解會開啟供編輯。

1. 以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [刪除註釋]。

   註解會遭到刪除。