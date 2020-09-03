---
title: PickBranch 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672578"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活動設計工具
<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。

## <a name="pickbranch"></a>PickBranch
 <xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick.Branches%2A> 活動的 <xref:System.Activities.Statements.Pick> 集合中。 每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。 透過這種方式，[!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供了事件架構的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具
 [ **PickBranch** ] 設計工具位於 [**工具箱**] 的 [**控制流程**] 類別中，若要存取，請按一下 (上的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X) 。

 <xref:System.Activities.Statements.PickBranch>當 Pick 活動設計工具一開始卸載至時，預設會建立兩個具有**Branch1**和**就 branch2**之顯示名稱的空白物件作為活動的元素 <xref:System.Activities.Statements.Pick> **Pick** [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。 這些個別 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 的屬性值可以在 **PickBranch** 設計工具標頭中編輯，也可以在每個分支的 [ **屬性** ] 視窗中編輯。

 有兩種方式可以將 <xref:System.Activities.Statements.PickBranch> 物件加入至物件的集合 <xref:System.Activities.Statements.Pick> ：從 [工具箱] 拖放 [ **PickBranch** ] 設計 **工具** ，或是從 **挑選** 設計介面中使用內容功能表：

1. **PickBranch** <xref:System.Activities.Statements.PickBranch> 當它從 [**工具箱**] 拖曳出來，放到介面上的 [ **Pick** ] 活動設計工具其中一個分支時，PickBranch 設計工具就會建立 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。 新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。 當您使用滑鼠將 **PickBranch** 設計工具拖曳至 **Pick** 設計工具時， **Pick** 設計工具會使用垂直藍灰色的寬線來指出 <xref:System.Activities.Statements.PickBranch> 針對特定滑鼠位置加入的位置。

2. 以滑鼠右鍵按一下 [ **挑選** 活動設計工具] (，但不在 [ **PickBranch** 設計師]) 中，以取得內容功能表並選取 [ **建立分支** ] 以加入新的 <xref:System.Activities.Statements.PickBranch> 。 請注意，新的 <xref:System.Activities.Statements.PickBranch> 會新增至 <xref:System.Activities.Statements.PickBranch> **Pick** 設計工具中現有物件的右邊。

   **PickBranch**設計工具可以展開，以顯示 [**觸發**程式] 和 [**動作**] 方塊，或按一下其標頭右邊的雙游標來折迭。 將 <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> <xref:System.Activities.Statements.PickBranch> 活動放入其設計工具的 [ **觸發** 程式] 和 [ **動作** ] 方塊中，以編輯每個的和。

   <xref:System.Activities.Statements.PickBranch>物件集合中的物件可以藉由將物件 <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.Pick> 拖曳至**Pick**設計工具中的新位置來重新排序。 **Pick**設計工具會使用垂直藍灰色的寬線來指出 <xref:System.Activities.Statements.PickBranch> 針對特定滑鼠位置加入的位置。

   有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：

3. 選取 [ **PickBranch** ] 設計工具，並將它刪除。

4. 選取 [ **PickBranch** ] 設計工具，以滑鼠右鍵按一下以取得內容功能表，然後選取 [ **刪除**]。

   請務必選取 [ **PickBranch** ] 設計工具，因為不小心選取其 **觸發** 程式或 **動作** 方塊內的其中一個活動，就會刪除其中一項活動，而不是 <xref:System.Activities.Statements.PickBranch> 物件。

### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流程設計工具中的 PickBranch 屬性
 下表顯示最實用的 <xref:System.Activities.Statements.PickBranch> 屬性，並且說明它們在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|否|**PickBranch**設計工具標頭上顯示的易記名稱。 預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|是|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|否|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|

## <a name="see-also"></a>另請參閱
 [使用 Pick 活動](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)[控制流程](../workflow-designer/control-flow-activity-designers.md)[挑選活動](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)