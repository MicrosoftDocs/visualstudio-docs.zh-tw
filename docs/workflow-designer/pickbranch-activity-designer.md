---
title: 工作流程設計工具 PickBranch 活動設計工具
description: 瞭解 PickBranch 活動設計工具如何在可由傳入事件觸發的 Pick 活動內，提供以事件為基礎的執行路徑。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d3ac314d5f8eb7980bdf5102d871546d3167141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968667"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 活動設計工具

<xref:System.Activities.Statements.PickBranch> 在 <xref:System.Activities.Statements.Pick> 活動內提供了以事件為依據的執行路徑，可由傳入的事件觸發。

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> 物件包含在一個 <xref:System.Activities.Statements.Pick.Branches%2A> 活動的 <xref:System.Activities.Statements.Pick> 集合中。 每一個 <xref:System.Activities.Statements.PickBranch> 都包含在 <xref:System.Activities.Statements.Pick> 活動的分支中，而且可以因為部分做為觸發程序的傳入事件而執行。 如此一來，工作流程設計工具提供事件型控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具

存取 [工具箱] 的 [**控制流程**] 類別中的 [ **PickBranch** ] 設計 **工具**。

<xref:System.Activities.Statements.PickBranch>   <xref:System.Activities.Statements.Pick> 當 **Pick** 活動設計工具最初放入工作流程設計工具時，預設會建立兩個具有 Branch1 和就 branch2 之顯示名稱的空白物件作為活動的元素。 這些個別 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 的屬性值可以在 **PickBranch** 設計工具標頭中編輯，也可以在每個分支的 [ **屬性** ] 視窗中編輯。

有兩種方式可以將 <xref:System.Activities.Statements.PickBranch> 物件加入至物件的集合 <xref:System.Activities.Statements.Pick> ：從 [工具箱] 拖放 [ **PickBranch** ] 設計 **工具**，或使用 [ **Pick** ] 設計介面中的右鍵功能表：

- 當 **PickBranch** 設計 <xref:System.Activities.Statements.PickBranch> 工具從 [ **工具箱** ] 拖曳出來，放入工作流程設計工具介面上 [ **Pick** ] 活動設計工具的其中一個分支時，就會建立。 新的 <xref:System.Activities.Statements.PickBranch> 物件可以放在 <xref:System.Activities.Statements.Pick> 設計工具內部，置於已經包含在集合中的任何現有 <xref:System.Activities.Statements.PickBranch> 項目的左邊或右邊。 當您使用滑鼠將 **PickBranch** 設計工具拖曳至 **Pick** 設計工具時， **Pick** 設計工具會使用垂直藍灰色的寬線來指出 <xref:System.Activities.Statements.PickBranch> 針對特定滑鼠位置加入的位置。

- 以滑鼠右鍵按一下 [ **挑選** 活動設計工具] (，但不在 [ **PickBranch** 設計師]) 中，以取得內容功能表並選取 [ **建立分支** ] 以加入新的 <xref:System.Activities.Statements.PickBranch> 。 請注意，新的 <xref:System.Activities.Statements.PickBranch> 會新增至 <xref:System.Activities.Statements.PickBranch> **Pick** 設計工具中現有物件的右邊。

**PickBranch** 設計工具可以展開，以顯示 [**觸發** 程式] 和 [**動作**] 方塊，或按一下其標頭右邊的雙游標來折迭。 將 <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> <xref:System.Activities.Statements.PickBranch> 活動放入其設計工具的 [ **觸發** 程式] 和 [ **動作** ] 方塊中，以編輯每個的和。

<xref:System.Activities.Statements.PickBranch>物件集合中的物件可以藉由將物件 <xref:System.Activities.Statements.Pick.Branches%2A> <xref:System.Activities.Statements.Pick> 拖曳至 **Pick** 設計工具中的新位置來重新排序。 **Pick** 設計工具會使用垂直藍灰色的寬線來指出 <xref:System.Activities.Statements.PickBranch> 針對特定滑鼠位置加入的位置。

有兩個方法可以刪除 <xref:System.Activities.Statements.PickBranch>：

- 選取 [ **PickBranch** ] 設計工具，並將它刪除。
- 選取 [ **PickBranch** ] 設計工具，以滑鼠右鍵按一下以取得內容功能表，然後選取 [ **刪除**]。

請務必選取 [ **PickBranch** ] 設計工具，因為不小心選取其 **觸發** 程式或 **動作** 方塊內的其中一個活動，就會刪除其中一項活動，而不是 <xref:System.Activities.Statements.PickBranch> 物件。

### <a name="pickbranch-properties-in-the-workflow-designer"></a>工作流程設計工具中的 PickBranch 屬性

下表顯示最有用的 <xref:System.Activities.Statements.PickBranch> 屬性，並說明如何在工作流程設計工具中使用它們。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|否|**PickBranch** 設計工具標頭上顯示的易記名稱。 預設值是 Branch。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|是|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 動作，可以叫用 <xref:System.Activities.Statements.PickBranch.Action%2A>。|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|否|各個 <xref:System.Activities.Statements.PickBranch> 都包含一個 <xref:System.Activities.Statements.PickBranch.Action%2A>，如果觸發就會執行。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [Pick 活動](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [使用 Pick 活動](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)