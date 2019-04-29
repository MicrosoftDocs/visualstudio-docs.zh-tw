---
title: 工作流程設計工具-FinalState 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8292e22bac6063a36286930584e1d7c227913511
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949684"
---
# <a name="finalstate-activity-designer"></a>FinalState 活動設計工具

<xref:System.Activities.Core.Presentation.FinalState> 設計工具是用來建立會終止狀態機器執行個體的 <xref:System.Activities.Statements.State>。

## <a name="using-the-finalstate-activity-designer"></a>使用 FinalState 活動設計工具

**FinalState**設計工具用來建立<xref:System.Activities.Statements.State>預先設定為終止狀態機器中的狀態。 A<xref:System.Activities.Statements.State>建立使用<xref:System.Activities.Core.Presentation.FinalState>活動設計工具有其<xref:System.Activities.Statements.State.IsFinal%2A>屬性設定為 **，則為 true**，沒有任何<xref:System.Activities.Statements.State.Exit%2A>活動和轉換源自於此。 若要使用<xref:System.Activities.Core.Presentation.FinalState>活動設計工具加入<xref:System.Activities.Statements.State>預先設定為狀態機器中的終止狀態的活動拖曳**FinalState**活動設計工具，從**狀態機器**一節**工具箱**拖放到工作流程設計工具。 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具可以放到 <xref:System.Activities.Statements.StateMachine> 和稍後加入的轉換，或是可以在放置 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具時建立轉換。 如需有關如何建立轉換的詳細資訊，請參閱 <<c0> [ 轉換](../workflow-designer/transition-activity-designer.md)。

### <a name="state-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 State 活動屬性

下表顯示可使用 <xref:System.Activities.Core.Presentation.FinalState> 設計工具設定的屬性，並說明如何在設計工具中使用它們。 其中一些屬性可以在屬性方格中進行編輯，有些可以在設計工具介面上編輯。

|屬性名稱|必要|使用量|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.State> 活動設計工具在標頭中的易記名稱。 預設值是**狀態**。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Statements.State.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Statements.State.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.State.Entry%2A>|False|指定此狀態在轉換時發生的動作。 這個值可以藉由拖曳 將活動從設定**工具箱**並放到<xref:System.Activities.Statements.State.Entry%2A>狀態一節。|

## <a name="see-also"></a>另請參閱

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [狀態](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)