---
title: 工作流程設計工具 PickBranch 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a43fa99c9f5fe4fbb3cfe336efb983fced655f2a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650062"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活動設計工具

<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick.Branches%2A> 活動的 <xref:System.Activities.Statements.Pick> 集合中。 每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。 如此一來，工作流程設計工具就會提供以事件為基礎的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具

在 [工具箱] 的 [**控制流程**] 分類中，存取 [ **PickBranch** ] 設計**工具**。

[ **Pick** ] 活動設計工具一開始放在工作流程設計工具上時，預設會建立兩個空白 <xref:System.Activities.Statements.PickBranch> 物件，其中包含**Branch1**和**就 branch2**的顯示名稱做為 <xref:System.Activities.Statements.Pick> 活動的元素。 這些個別的 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 屬性值可以在**PickBranch**設計工具標頭中編輯，或是在每個分支的 [**屬性**] 視窗中編輯。

有兩種方式可以將 <xref:System.Activities.Statements.PickBranch> 物件加入 <xref:System.Activities.Statements.Pick> 物件的集合：從 [工具箱] 拖放 [ **PickBranch** ] 設計**工具**，或使用 [**挑選**] 設計介面中的右鍵功能表：

- **PickBranch**設計工具會在從 [**工具箱**] 拖曳並放到工作流程設計工具介面上的 [ **Pick** ] 活動設計工具的其中一個分支時，建立 <xref:System.Activities.Statements.PickBranch>。 新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。 當您使用滑鼠將 [ **PickBranch** ] 設計工具拖曳至 [ **pick** ] 設計工具時，[**選擇**設計工具] 會使用垂直藍灰色的寬線來表示針對特定滑鼠位置加入 <xref:System.Activities.Statements.PickBranch>。

- 以滑鼠右鍵按一下 [ **Pick** ] 活動設計工具（但不在**PickBranch**表設計工具內）以取得操作功能表，然後選取 [**建立分支**] 以加入新的 <xref:System.Activities.Statements.PickBranch>。 請注意，新的 <xref:System.Activities.Statements.PickBranch> 會加入至**Pick**設計工具中現有 <xref:System.Activities.Statements.PickBranch> 物件的右邊。

**PickBranch**設計工具可以展開，以顯示**觸發**程式和**動作**方塊，或按一下標題右邊的雙插入號來折迭。 藉由將活動放入其設計工具的 [**觸發**程式] 和 [**動作**] 方塊中，編輯每個 <xref:System.Activities.Statements.PickBranch> 的 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 和 <xref:System.Activities.Statements.PickBranch.Action%2A>。

在 <xref:System.Activities.Statements.Pick> 物件之 <xref:System.Activities.Statements.Pick.Branches%2A> 集合中的 <xref:System.Activities.Statements.PickBranch> 物件，可以藉由將其拖放到**Pick**設計工具內的新位置來重新排序。 **Pick**設計工具會使用垂直藍灰色的寬線，來指出要為指定的滑鼠位置加入 <xref:System.Activities.Statements.PickBranch>。

有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：

- 選取 [ **PickBranch** ] 設計工具，並將它刪除。
- 選取 [ **PickBranch** ] 設計工具，以滑鼠右鍵按一下以取得內容功能表，然後選取 [**刪除**]。

請務必選取 [ **PickBranch** ] 設計工具，因為在其 [**觸發**程式] 或 [**動作**] 方塊中選取其中一個活動時，不會刪除其中一個活動，而非 [<xref:System.Activities.Statements.PickBranch>] 物件。

### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流程設計工具中的 PickBranch 屬性

下表顯示最有用的 <xref:System.Activities.Statements.PickBranch> 屬性，並說明如何在工作流程設計工具中使用它們。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|在**PickBranch**設計工具的標頭上顯示的易記名稱。 預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|

## <a name="see-also"></a>請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [挑選活動](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [使用 Pick 活動](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)