---
title: 如何：將批註加入至工作流程設計工具中的工作流程 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663456"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>HOW TO：將註解新增至工作流程設計工具中的工作流程
為了方便建立更大型、更為複雜的工作流程，[!INCLUDE[net_v45](../includes/net-v45-md.md)] 讓開發人員可以在設計工具中將註釋加入到下列項目類型：

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- 衍生自 <xref:System.Activities.Statements.FlowNode> 的類別

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> 註釋的內容會以純文字的格式儲存在與工作流程相關聯 XAML 檔中，並有可能被其他人讀取。 將敏感資訊輸入至註釋時要謹慎。

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>將註釋加入到設計工具中的活動

1. 在工作流程設計工具中，以滑鼠右鍵按一下工作流程設計工具中的專案，然後選取 [**注釋**]、[**加入批註**]。

2. 在提供的空間中加入註釋的文字。

3. 該項目將顯示註釋圖示。 將滑鼠停留在註釋圖示上會顯示註釋的文字。

     ![顯示注釋的序列活動](../workflow-designer/media/annotation.png "註釋")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>在活動的設計工具中顯示註釋

1. 如果活動設計工具具有顯示在活動外部的注釋，請按一下注釋裝飾項中的**釘**選圖示。

2. 註釋將顯示在活動的設計工具中。 在下列螢幕擷取畫面中，註釋「工作流程中的開始活動」顯示在活動的設計工具中。

     ![活動設計工具中顯示的注釋](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

3. 若要在活動的設計工具外部顯示注釋，請將滑鼠停留在活動設計工具中的注釋區域上，然後按一下 [**取消**釘選] 圖示。

     ![顯示在活動設計師外部的注釋](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>顯示或隱藏所有註釋

1. 以滑鼠右鍵按一下具有註釋的活動。 選取 [**注釋**]、[**顯示所有注釋**]。

2. 所有註釋將顯示在活動的設計工具中。

3. 若要顯示活動設計工具以外的所有批註，請以滑鼠右鍵按一下活動，然後選取 [**注釋**]、[**隱藏所有注釋**]。

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>編輯或刪除活動的註釋

1. 以滑鼠右鍵按一下具有註釋的活動。

2. 選取 [**注釋**]、[**編輯注釋**] 或 [**刪除注釋**]。

3. 將開啟註釋以進行編輯或刪除。

4. 若要一次刪除所有注釋，請以滑鼠右鍵按一下工作流程設計工具，並選取 [**注釋**]、[**刪除所有注釋**]。

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>加入、編輯和刪除變數或引數的註釋

1. 以滑鼠右鍵按一下變數或引數，並選取 [新增註釋]。

2. 輸入註釋的文字。 變數或引數將顯示註釋圖示。

3. 以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [編輯註釋]。

4. 將開啟註釋以進行編輯。

5. 以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [刪除註釋]。

6. 註釋將被刪除。