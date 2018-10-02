---
title: Pick 活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d5bf361d2217c199fa2818a94c441e1d2b105e7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486101"
---
# <a name="pick-activity-designer"></a>Pick 活動設計工具
<xref:System.Activities.Statements.Pick> 活動會提供以事件為主的控制流程。 活動會執行若干分支的其中一個，以回應觸發的事件。  
  
## <a name="the-pick-activity"></a>Pick 活動  
 <xref:System.Activities.Statements.Pick> 活動包含 <xref:System.Activities.Statements.PickBranch> 物件的集合，<xref:System.Activities.Statements.Pick> 活動可因部分做為觸發的傳入事件而執行這些物件中的其中一個。 透過這種方式，[!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供了事件架構的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。 剛開始執行 <xref:System.Activities.Statements.Pick> 活動時，會排程 <xref:System.Activities.Statements.PickBranch> 項目的所有觸發活動。 第一個活動完成時，就會排程對應的動作活動，然後取消其他所有觸發活動。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具  
 **挑選**活動設計工具位於**控制流程**類別**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **挑選**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動設計工具通常用來放置，例如在**序列**活動設計工具。 置放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 上後，會建立 <xref:System.Activities.Statements.Pick> 活動，根據預設，此活動會包含兩個空的 <xref:System.Activities.Statements.PickBranch> 活動以做為會顯示 Branch1 和 Branch2 名稱的項目。 各自<xref:System.Activities.Statements.PickBranch.DisplayName%2A>屬性值可以在中編輯**PickBranch**活動設計工具的標頭或內**屬性**針對每個分支的視窗。  
  
 有兩種方式，以新增<xref:System.Activities.Statements.PickBranch>活動的集合<xref:System.Activities.Statements.Pick>物件： 拖曳和卸除**PickBranch**設計工具**工具箱**或使用中的內容功能表內**挑選**設計介面。 如需詳細資訊，請參閱 < [PickBranch](../workflow-designer/pickbranch-activity-designer.md)主題。 請注意，唯一項目可以置於**挑選**活動設計工具**PickBranch**活動設計工具。  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Pick 活動屬性  
 下表顯示 <xref:System.Activities.Statements.Pick> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Pick> 活動設計工具在標頭中的易記名稱。 預設值為 Pick。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
  
## <a name="see-also"></a>另請參閱  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)   
 [Pick 活動](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [使用 Pick 活動](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)