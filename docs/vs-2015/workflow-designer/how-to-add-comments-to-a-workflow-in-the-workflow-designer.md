---
title: 如何： 將註解加入至工作流程設計工具中的工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f70f8ba1a30d5adcaffe7e693fcc711d08a28baf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488759"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>HOW TO：將註解新增至工作流程設計工具中的工作流程
為了方便建立更大型、更為複雜的工作流程，[!INCLUDE[net_v45](../includes/net-v45-md.md)] 讓開發人員可以在設計工具中將註釋加入到下列項目類型：  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   衍生自 <xref:System.Activities.Statements.FlowNode> 的類別  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  註釋的內容會以純文字的格式儲存在與工作流程相關聯 XAML 檔中，並有可能被其他人讀取。 將敏感資訊輸入至註釋時要謹慎。  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>將註釋加入到設計工具中的活動  
  
1.  在工作流程設計工具中，以滑鼠右鍵按一下工作流程設計工具，並選取中的項目**註釋**，**加入註解**。  
  
2.  在提供的空間中加入註釋的文字。  
  
3.  該項目將顯示註釋圖示。 將滑鼠停留在註釋圖示上會顯示註釋的文字。  
  
     ![序列活動中顯示註釋](../workflow-designer/media/annotation.png "註釋")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>在活動的設計工具中顯示註釋  
  
1.  與活動設計工具的註釋顯示位於活動外部，按一下**Pin**註釋裝飾項中的圖示。  
  
2.  註釋將顯示在活動的設計工具中。 在下列螢幕擷取畫面中，註釋「工作流程中的開始活動」顯示在活動的設計工具中。  
  
     ![活動設計工具中顯示的註釋](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  若要顯示的活動設計工具外部註釋，將滑鼠停留在活動設計工具中的註釋區域，按一下**取消釘選**圖示  
  
     ![活動的設計工具外部顯示註釋](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>顯示或隱藏所有註釋  
  
1.  以滑鼠右鍵按一下具有註釋的活動。 選取 **註釋**，**顯示所有註釋**。  
  
2.  所有註釋將顯示在活動的設計工具中。  
  
3.  若要顯示的活動設計工具以外的所有註解，以滑鼠右鍵按一下活動，然後選取**註釋**，**隱藏所有註解**。  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>編輯或刪除活動的註釋  
  
1.  以滑鼠右鍵按一下具有註釋的活動。  
  
2.  選取 **註釋**，**編輯註釋**或是**刪除註解**。  
  
3.  將開啟註釋以進行編輯或刪除。  
  
4.  若要一次刪除所有註解，請以滑鼠右鍵按一下工作流程設計工具，並選取**註釋**，**刪除所有註解**。  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>加入、編輯和刪除變數或引數的註釋  
  
1.  以滑鼠右鍵按一下變數或引數，並選取 [新增註釋]。  
  
2.  輸入註釋的文字。 變數或引數將顯示註釋圖示。  
  
3.  以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [編輯註釋]。  
  
4.  將開啟註釋以進行編輯。  
  
5.  以滑鼠右鍵按一下具有註釋的變數或引數。 選取 [刪除註釋]。  
  
6.  註釋將被刪除。