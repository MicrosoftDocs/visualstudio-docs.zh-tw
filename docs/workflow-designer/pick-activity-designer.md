---
title: 工作流程設計工具-Pick 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd37c78567ea11d53899bcbaefb2e3809a00057
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826007"
---
# <a name="pick-activity-designer"></a>Pick 活動設計工具

<xref:System.Activities.Statements.Pick> 活動會提供以事件為主的控制流程。 活動會執行若干分支的其中一個，以回應觸發的事件。

## <a name="the-pick-activity"></a>Pick 活動

<xref:System.Activities.Statements.Pick> 活動包含 <xref:System.Activities.Statements.PickBranch> 物件的集合，<xref:System.Activities.Statements.Pick> 活動可因部分做為觸發的傳入事件而執行這些物件中的其中一個。 這種方式在工作流程設計工具會提供事件為基礎的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。 在開頭<xref:System.Activities.Statements.Pick>活動的執行中，所有觸發程序活動<xref:System.Activities.Statements.PickBranch>排程項目。 第一個活動完成時，就會排程對應的動作活動，然後取消其他所有觸發活動。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具

存取權**挑選**中的活動設計工具**控制流程**分類**工具箱**。 **挑選**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，只要通常放置活動設計工具，例如在**序列**活動設計工具。 後放入工作流程設計工具，它會建立<xref:System.Activities.Statements.Pick>活動，其中預設包含兩個空<xref:System.Activities.Statements.PickBranch>活動為具有項目會顯示 Branch1 和 Branch2 名稱。 各自<xref:System.Activities.Statements.PickBranch.DisplayName%2A>屬性值可以在中編輯**PickBranch**活動設計工具的標頭或內**屬性**針對每個分支的視窗。

有兩種方式，以新增<xref:System.Activities.Statements.PickBranch>活動的集合<xref:System.Activities.Statements.Pick>物件： 拖曳和卸除**PickBranch**設計工具**工具箱**或使用中的內容功能表內**挑選**設計介面。 如需詳細資訊，請參閱 < [PickBranch](../workflow-designer/pickbranch-activity-designer.md)主題。 請注意，唯一項目可以置於**挑選**活動設計工具**PickBranch**活動設計工具。

### <a name="pick-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Pick 活動屬性

下表顯示 <xref:System.Activities.Statements.Pick> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Pick> 活動設計工具在標頭中的易記名稱。 預設值為 Pick。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [挑選活動](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [使用 Pick 活動](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)