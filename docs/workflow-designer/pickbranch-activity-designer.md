---
title: 工作流程設計工具 PickBranch 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34da9091c0f96b7270678f9b36fe861e4a87418f
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876082"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活動設計工具

<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick.Branches%2A> 活動的 <xref:System.Activities.Statements.Pick> 集合中。 每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。 如此一來，工作流程設計工具就會提供以事件為基礎的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具

在 [工具箱] 的 [**控制流程**] 分類中，存取 [ **PickBranch** ] 設計**工具**。

<xref:System.Activities.Statements.PickBranch>[Pick] 活動設計工具一**Branch1** **Branch2** <xref:System.Activities.Statements.Pick> 開始放在工作流程設計工具上時，預設會建立兩個具有 Branch1 **Pick**和就 branch2 顯示名稱的空白物件做為活動的元素。 這些個別 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 的屬性值可以在**PickBranch**設計工具標頭中編輯，或是在每個分支的 [**屬性**] 視窗中進行編輯。

有兩種方式可以將 <xref:System.Activities.Statements.PickBranch> 物件加入至物件的集合 <xref:System.Activities.Statements.Pick> ：從 [工具箱] 拖放 [ **PickBranch** ] 設計**工具**，或使用 [**挑選**] 設計介面中的右鍵功能表：

- 當**PickBranch**表設計 <xref:System.Activities.Statements.PickBranch> 工具從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上的 [ **Pick** ] 活動設計工具的其中一個分支時，就會建立。 新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。 當您使用滑鼠將 [ **PickBranch** ] 設計工具拖曳至 [ **pick** ] 設計工具時，[**選擇**設計工具] 會使用垂直藍灰色的寬線來表示 <xref:System.Activities.Statements.PickBranch> 針對指定的滑鼠位置加入的位置。

- 以滑鼠右鍵按一下 [ **Pick** ] 活動設計工具（但不在**PickBranch**表設計工具內）以取得操作功能表，然後選取 [**建立分支**] 以加入新的 <xref:System.Activities.Statements.PickBranch> 。 請注意，新的 <xref:System.Activities.Statements.PickBranch> 會加入至 <xref:System.Activities.Statements.PickBranch> **Pick**設計工具中現有物件的右邊。

**PickBranch**設計工具可以展開，以顯示**觸發**程式和**動作**方塊，或按一下標題右邊的雙插入號來折迭。 藉 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 由將 <xref:System.Activities.Statements.PickBranch.Action%2A> <xref:System.Activities.Statements.PickBranch> 活動放入其設計工具的 [**觸發**程式] 和 [**動作**] 方塊中，編輯每個的和。

<xref:System.Activities.Statements.PickBranch>物件之集合中的物件 <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.Pick> ，可以藉由將其拖放到**Pick**設計工具內的新位置來重新排序。 **Pick**設計工具會使用垂直藍灰色的寬線，來表示 <xref:System.Activities.Statements.PickBranch> 針對指定的滑鼠位置新增的位置。

有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：

- 選取 [ **PickBranch** ] 設計工具，並將它刪除。
- 選取 [ **PickBranch** ] 設計工具，以滑鼠右鍵按一下以取得內容功能表，然後選取 [**刪除**]。

請務必選取 [ **PickBranch** ] 設計工具，因為在其 [**觸發**程式] 或 [**動作**] 方塊中選取其中一個活動時，不小心刪除了其中一個活動，而不是 <xref:System.Activities.Statements.PickBranch> 物件。

### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流程設計工具中的 PickBranch 屬性

下表顯示最有用的 <xref:System.Activities.Statements.PickBranch> 屬性，並說明如何在工作流程設計工具中使用它們。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|否|在**PickBranch**設計工具的標頭上顯示的易記名稱。 預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|是|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|否|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [Pick 活動](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [使用 Pick 活動](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)