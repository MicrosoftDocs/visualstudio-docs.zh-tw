---
title: 工作流程設計工具-Pick 活動設計工具
description: 瞭解 Pick 活動如何提供以事件為基礎的控制流程，並執行數個分支中的其中一個來回應觸發的事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b616cf3d9b7eba5b2a2e9de23546a8a5f9c36ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968693"
---
# <a name="pick-activity-designer"></a>Pick 活動設計工具

<xref:System.Activities.Statements.Pick> 活動會提供以事件為主的控制流程。 活動會執行若干分支的其中一個，以回應觸發的事件。

## <a name="the-pick-activity"></a>Pick 活動

<xref:System.Activities.Statements.Pick> 活動包含 <xref:System.Activities.Statements.PickBranch> 物件的集合，<xref:System.Activities.Statements.Pick> 活動可因部分做為觸發的傳入事件而執行這些物件中的其中一個。 如此一來工作流程設計工具提供事件型控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。 在活動執行開始時 <xref:System.Activities.Statements.Pick> ，會排程專案的所有觸發程式活動 <xref:System.Activities.Statements.PickBranch> 。 第一個活動完成時，就會排程對應的動作活動，然後取消其他所有觸發活動。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具

存取 [工具箱] 的 [**控制流程**] 類別中的 [ **Pick** ] 活動設計 **工具**。 [ **Pick** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動設計工具的任一處，例如在 [ **Sequence** ] 活動設計工具內部。 將它放入工作流程設計工具之後，它會建立 <xref:System.Activities.Statements.Pick> 活動，此活動預設會將兩個空白的 <xref:System.Activities.Statements.PickBranch> 活動包含為 Branch1 和就 branch2 的顯示名稱的元素。 這些個別 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 的屬性值可以在 [ **PickBranch** ] 活動設計工具標頭中編輯，或是在每個分支的 [ **屬性** ] 視窗中編輯。

有兩種方式可將 <xref:System.Activities.Statements.PickBranch> 活動加入至物件的集合 <xref:System.Activities.Statements.Pick> ：從 [工具箱] 拖放 [ **PickBranch** ] 設計 **工具** ，或使用 [ **挑選** ] 設計介面中的右鍵功能表。 如需詳細資訊，請參閱 [PickBranch](../workflow-designer/pickbranch-activity-designer.md) 主題。 請注意，唯一可放置在 **Pick** 活動設計工具內的專案是 **PickBranch** 活動設計工具。

### <a name="pick-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Pick 活動屬性

下表顯示 <xref:System.Activities.Statements.Pick> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.Pick> 活動設計工具在標頭中的易記名稱。 預設值為 Pick。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|

## <a name="see-also"></a>另請參閱

- [控制流程](../workflow-designer/control-flow-activity-designers.md)
- [Pick 活動](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [使用 Pick 活動](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)