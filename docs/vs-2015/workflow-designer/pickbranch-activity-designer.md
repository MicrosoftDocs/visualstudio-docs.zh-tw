---
title: PickBranch 活動設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f39479c9421ab87caf7c918e05be89272f0fb4de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887299"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活動設計工具
<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick.Branches%2A> 活動的 <xref:System.Activities.Statements.Pick> 集合中。 每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。 透過這種方式，[!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供了事件架構的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具  
 **PickBranch**設計工具位於**控制流程**類別**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X)。  
  
 兩個空<xref:System.Activities.Statements.PickBranch>物件，顯示名稱**Branch1**並**Branch2**項目預設會建立<xref:System.Activities.Statements.Pick>活動時**挑選**活動設計工具一開始放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]。 各自<xref:System.Activities.Statements.PickBranch.DisplayName%2A>屬性值可以在中編輯**PickBranch**設計工具的標頭或內**屬性**針對每個分支的視窗。  
  
 有兩種方式，以新增<xref:System.Activities.Statements.PickBranch>物件的集合<xref:System.Activities.Statements.Pick>物件： 拖曳和卸除**PickBranch**設計工具**工具箱**或使用中的內容功能表內**挑選**設計介面：  
  
1. **PickBranch**設計工具會建立<xref:System.Activities.Statements.PickBranch>當從拖曳**工具箱**然後放到其中的分支**挑選**上的活動設計工具[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面。 新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。 拖曳時**PickBranch**設計工具拖曳到**挑選**滑鼠，設計工具**挑選**設計工具會使用垂直的藍灰色帶，來表示<xref:System.Activities.Statements.PickBranch>加入某個特定的滑鼠位置。  
  
2. 以滑鼠右鍵按一下**挑選**活動設計工具 (但不是深入探討**PickBranch**設計工具) 來取得內容功能表，再選取**Create Branch**來新增新的<xref:System.Activities.Statements.PickBranch>。 請注意，新<xref:System.Activities.Statements.PickBranch>新增至現有的權限<xref:System.Activities.Statements.PickBranch>中的物件**挑選**設計工具。  
  
   **PickBranch**設計工具可以展開以顯示**觸發程序**並**動作**方塊，若要摺疊，只要按一下各個標題右邊的雙箭頭符號即可。 編輯<xref:System.Activities.Statements.PickBranch.Trigger%2A>並<xref:System.Activities.Statements.PickBranch.Action%2A>每個<xref:System.Activities.Statements.PickBranch>活動放進**觸發程序**並**動作**其設計工具的方塊。  
  
   <xref:System.Activities.Statements.PickBranch>中的物件<xref:System.Activities.Statements.Pick.Branches%2A>的集合<xref:System.Activities.Statements.Pick>物件，可以藉由拖放到新的位置中重新排列**挑選**設計工具。 **挑選**設計工具會使用垂直的藍灰色帶，來表示<xref:System.Activities.Statements.PickBranch>加入某個特定的滑鼠位置。  
  
   有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：  
  
3. 選取  **PickBranch**設計工具並將它刪除。  
  
4. 選取 [ **PickBranch**設計師] 中，按一下滑鼠右鍵取得操作功能表，然後選取**刪除**。  
  
   務必選取**PickBranch**設計工具，因為其中一個內活動及其**觸發程序**或**動作**方塊不小心刪除其中的活動而非<xref:System.Activities.Statements.PickBranch>物件。  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流程設計工具中的 PickBranch 屬性  
 下表顯示最實用的 <xref:System.Activities.Statements.PickBranch> 屬性，並且說明它們在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中的使用方式。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|標頭上顯示的易記名稱**PickBranch**設計工具。 預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|  
  
## <a name="see-also"></a>另請參閱  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)   
 [Pick 活動](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [使用 Pick 活動](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)