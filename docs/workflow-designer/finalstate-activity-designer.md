---
title: 工作流程設計工具 FinalState 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: b8f25167f3a67e2d1349354ce568c076697e3e73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650465"
---
# <a name="finalstate-activity-designer"></a>FinalState 活動設計工具

<xref:System.Activities.Core.Presentation.FinalState> 設計工具是用來建立會終止狀態機器執行個體的 <xref:System.Activities.Statements.State>。

## <a name="using-the-finalstate-activity-designer"></a>使用 FinalState 活動設計工具

**FinalState**設計工具是用來建立在狀態機器中預先設定為終止狀態的 <xref:System.Activities.Statements.State>。 使用 [<xref:System.Activities.Core.Presentation.FinalState>] 活動設計工具所建立的 <xref:System.Activities.Statements.State>，其 <xref:System.Activities.Statements.State.IsFinal%2A> 屬性設定為**true**，沒有 <xref:System.Activities.Statements.State.Exit%2A> 活動，而且沒有來自它的轉換。 若要使用 [<xref:System.Activities.Core.Presentation.FinalState>] 活動設計工具加入在狀態機器中預先設定為終止狀態的 <xref:System.Activities.Statements.State> 活動，請從 [工具箱] 的 [**狀態機器**] 區段中，將 [ **FinalState** ] 活動設計**工具**拖放到工作流程設計工具。 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具可以放到 <xref:System.Activities.Statements.StateMachine> 和稍後加入的轉換，或是可以在放置 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具時建立轉換。 如需建立轉換的詳細資訊，請參閱[轉換](../workflow-designer/transition-activity-designer.md)。

### <a name="state-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 State 活動屬性

下表顯示可使用 <xref:System.Activities.Core.Presentation.FinalState> 設計工具設定的屬性，並說明如何在設計工具中使用它們。 其中一些屬性可以在屬性方格中進行編輯，有些可以在設計工具介面上編輯。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|偽|指定 <xref:System.Activities.Statements.State> 活動設計工具在標頭中的易記名稱。 預設值為**State**。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Statements.State.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Statements.State.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.State.Entry%2A>|偽|指定此狀態在轉換時發生的動作。 從 [**工具箱**] 拖曳活動並放到狀態的 [<xref:System.Activities.Statements.State.Entry%2A>] 區段，即可設定此值。|

## <a name="see-also"></a>另請參閱

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [狀態](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)