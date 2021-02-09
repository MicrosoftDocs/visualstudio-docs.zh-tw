---
title: 工作流程設計工具狀態活動設計工具
description: 瞭解「StateMachine」活動，以及如何使用 [狀態] 活動設計工具將狀態加入至工作流程。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: abf4e81ecd258668c93b674410f029e6be0f5bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873511"
---
# <a name="state-activity-designer"></a>狀態活動設計工具

<xref:System.Activities.Statements.State> 代表狀態機器可以具有的狀態。

## <a name="using-the-state-activity-designer"></a>使用 State 活動設計工具

若要將加入 <xref:System.Activities.Statements.State> 至工作流程，請從 [工具箱] 的 [**狀態機器**] 區段中，將 [**狀態**] 活動設計 **工具** 拖放至 <xref:System.Activities.Statements.StateMachine> 工作流程設計工具介面上的活動。 <xref:System.Activities.Statements.State> 活動稍後可以放到 <xref:System.Activities.Statements.StateMachine> 和加入的轉換，或是可以在放置 <xref:System.Activities.Statements.State> 活動時建立轉換。 若要 <xref:System.Activities.Statements.State> 在一個步驟中加入活動並建立轉換，請從 [工具箱] 的 **[狀態機器**] 區段中拖曳 [**狀態**] 活動，並將其停留在工作流程設計 **工具** 中的另一個狀態。 當被拖曳的 <xref:System.Activities.Statements.State> 位在另一個 <xref:System.Activities.Statements.State> 上方時，另一個 <xref:System.Activities.Statements.State> 周圍會出現四個三角形。 如果將 <xref:System.Activities.Statements.State> 拖放到四個三角形的其中一個，就會將它加入到該狀態機器，並建立從來源 <xref:System.Activities.Statements.State> 到所放置之目的地 <xref:System.Activities.Statements.State> 的轉換。 如需詳細資訊，請參閱 [轉換](../workflow-designer/transition-activity-designer.md)。

### <a name="state-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 State 活動屬性

下表顯示可使用工作流程設計工具設定的 <xref:System.Activities.Statements.State> 屬性，並說明如何在設計工具中使用它們。 其中一些屬性可以在屬性方格中進行編輯，有些可以在設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.State> 活動設計工具在標頭中的易記名稱。 預設值為 [ **狀態**]。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Statements.State.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Statements.State.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.State.Entry%2A>|否|指定此狀態在轉換時發生的動作。 當 <xref:System.Activities.Statements.State> 活動展開時，可以將活動從 [ **工具箱** ] 拖曳到狀態的 [ **專案** ] 區段，藉以設定這個值。|
|<xref:System.Activities.Statements.State.Exit%2A>|否|指定此狀態在轉換時發生的動作。 當 <xref:System.Activities.Statements.State> 活動展開時，可以將活動從 [ **工具箱** ] 拖曳到狀態的 [結束] 區段 **，藉** 以設定這個值。|
|<xref:System.Activities.Statements.State.Transitions%2A>|否|列出來自 <xref:System.Activities.Statements.State> 的可能轉換。 清單中的每個項目都有指向關聯的 <xref:System.Activities.Statements.Transition> 和目的地 <xref:System.Activities.Statements.State> 的連結。 按一下此連結會將設計工具切換到 <xref:System.Activities.Statements.Transition> 或 <xref:System.Activities.Statements.State> 的展開檢視。|

## <a name="see-also"></a>另請參閱

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [轉換](../workflow-designer/transition-activity-designer.md)
