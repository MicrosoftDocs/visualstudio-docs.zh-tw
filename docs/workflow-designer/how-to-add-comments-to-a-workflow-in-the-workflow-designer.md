---
title: 工作流程設計工具-如何：將批註新增至工作流程
description: 瞭解 .NET Framework 4.5 如何讓開發人員將批註加入至設計工具中的特定專案類型，例如活動、狀態和轉換專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 9417dd0084b381d8fc997a90b4690c49191f4785
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971696"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>HOW TO：將註解新增至工作流程設計工具中的工作流程

為了方便建立更大型、更複雜的工作流程，.NET Framework 4.5 可讓開發人員在設計工具中將批註新增至下列類型的專案：

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- 衍生自 <xref:System.Activities.Statements.FlowNode> 的類別

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> 註釋的內容會以純文字的格式儲存在與工作流程相關聯 XAML 檔中，並有可能被其他人讀取。 將敏感資訊輸入至註釋時要謹慎。

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>將註釋加入到設計工具中的活動

1. 在工作流程設計工具中，以滑鼠右鍵按一下工作流程設計工具中的專案，然後選取 [ **注釋**]、[ **加入批註**]。

1. 在提供的空間中加入註釋的文字。

   專案會顯示注釋圖示。 將滑鼠停留在批註圖示上會顯示注釋的文字。

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>在活動的設計工具中顯示註釋

1. 使用活動設計工具，其批註顯示在活動之外，請按一下批註裝飾項中的 **釘** 選圖示。

   批註會顯示在活動的設計工具中。 在下列螢幕擷取畫面中，註釋「工作流程中的開始活動」顯示在活動的設計工具中。

   ![在活動設計工具中顯示的註釋](../workflow-designer/media/annotationindesigner.png)

2. 若要在活動的設計工具外部顯示批註，請將滑鼠停留在活動設計工具中的注釋區域上方，然後按一下 [ **取消** 釘選] 圖示

   ![顯示在活動設計工具之外的注釋](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>顯示或隱藏所有註釋

1. 以滑鼠右鍵按一下具有註釋的活動。 選取 [ **注釋**]、[ **顯示所有注釋**]。

   所有批註都會顯示在活動的設計工具中。

1. 若要顯示活動設計工具以外的所有批註，請以滑鼠右鍵按一下活動，然後選取 [ **注釋**]、[ **隱藏所有注釋**]。

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>編輯或刪除活動的註釋

1. 以滑鼠右鍵按一下具有註釋的活動。

1. 選取 [ **注釋**]、[ **編輯批註** ] 或 [ **刪除注釋**]。

   批註會開啟以供編輯或刪除。

1. 若要一次刪除所有批註，請以滑鼠右鍵按一下工作流程設計工具，然後選取 [ **注釋**]、[ **刪除所有注釋**]。

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>加入、編輯和刪除變數或引數的註釋

1. 以滑鼠右鍵按一下變數或引數，並選取 [新增註釋]。

1. 輸入註釋的文字。 變數或引數會顯示注釋圖示。

1. 以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [編輯註釋]。

   批註會開啟以供編輯。

1. 以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [刪除註釋]。

   批註會被刪除。
