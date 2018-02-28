---
title: "PickBranch 活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: d583c662de31b990982b78d876bc0046e89089d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活動設計工具
<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick.Branches%2A> 活動的 <xref:System.Activities.Statements.Pick> 集合中。 每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。 透過這種方式，[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 提供了事件架構的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。  
  
### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具  
 **PickBranch**設計工具位於**控制流程**分類**工具箱**，即可存取的哪一個**工具箱**索引標籤上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X)。  
  
 兩個空<xref:System.Activities.Statements.PickBranch>物件與顯示名稱的**Branch1**和**Branch2**做為的項目建立的預設<xref:System.Activities.Statements.Pick>活動時**挑選**活動設計工具一開始放入[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]。 這些個別<xref:System.Activities.Statements.PickBranch.DisplayName%2A>屬性值可以在中編輯**PickBranch**設計工具標頭或**屬性**針對每個分支的視窗。  
  
 有兩種方式新增<xref:System.Activities.Statements.PickBranch>物件的集合<xref:System.Activities.Statements.Pick>物件： 拖曳和卸除**PickBranch**設計工具從**工具箱**或使用中的內容功能表內**挑選**設計介面：  
  
1.  **PickBranch**設計工具會建立<xref:System.Activities.Statements.PickBranch>時從拖曳**工具箱**並放入每個分支的**挑選**上的活動設計工具[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面。 新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。 拖曳時**PickBranch**設計工具拖曳到**挑選**設計工具，使用滑鼠，**挑選**設計工具會使用垂直的藍灰色帶，以指示<xref:System.Activities.Statements.PickBranch>會加入為某個特定的滑鼠位置。  
  
2.  以滑鼠右鍵按一下**挑選**活動設計工具 (但不是在**PickBranch**設計工具) 來取得內容功能表並選取**建立分支**即可新增<xref:System.Activities.Statements.PickBranch>。 請注意，新<xref:System.Activities.Statements.PickBranch>現存的右邊就會加入<xref:System.Activities.Statements.PickBranch>中的物件**挑選**設計工具。  
  
 **PickBranch**設計工具可以展開以顯示**觸發程序**和**動作**方塊或摺疊，只要按一下其標頭右邊 double 的插入號。 編輯<xref:System.Activities.Statements.PickBranch.Trigger%2A>和<xref:System.Activities.Statements.PickBranch.Action%2A>每個<xref:System.Activities.Statements.PickBranch>由活動放進**觸發程序**和**動作**其設計工具的方塊。  
  
 <xref:System.Activities.Statements.PickBranch>中的物件<xref:System.Activities.Statements.Pick.Branches%2A>集合<xref:System.Activities.Statements.Pick>物件，可以重新排列拖曳和卸除它們中的新位置**挑選**設計工具。 **挑選**設計工具會使用垂直的藍灰色帶，以指示<xref:System.Activities.Statements.PickBranch>加入為某個特定的滑鼠位置。  
  
 有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：  
  
1.  選取**PickBranch**設計工具並將它刪除。  
  
2.  選取**PickBranch**設計工具中，按一下滑鼠右鍵，以取得操作功能表，再選取**刪除**。  
  
 請務必選取**PickBranch**設計工具中，選取其中一個內的活動其**觸發程序**或**動作**方塊不小心刪除其中的活動而非<xref:System.Activities.Statements.PickBranch>物件。  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流程設計工具中的 PickBranch 屬性  
 下表顯示最實用的 <xref:System.Activities.Statements.PickBranch> 屬性，並且說明它們在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 中的使用方式。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|標頭上顯示的易記名稱**PickBranch**設計工具。 預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|  
  
## <a name="see-also"></a>請參閱  
 [控制流程](../workflow-designer/control-flow-activity-designers.md)   
 [Pick 活動](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [使用 Pick 活動](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)