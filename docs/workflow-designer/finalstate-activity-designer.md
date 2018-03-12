---
title: "FinalState 活動設計工具 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a5b9b8cc1fc0bdb390e1bf32a6a8f262b435a157
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="finalstate-activity-designer"></a>FinalState 活動設計工具
<xref:System.Activities.Core.Presentation.FinalState> 設計工具是用來建立會終止狀態機器執行個體的 <xref:System.Activities.Statements.State>。

## <a name="using-the-finalstate-activity-designer"></a>使用 FinalState 活動設計工具
 **FinalState**設計工具用於建立<xref:System.Activities.Statements.State>預先設定為終止狀態機器中的狀態。 A<xref:System.Activities.Statements.State>建立<xref:System.Activities.Core.Presentation.FinalState>活動設計工具有其<xref:System.Activities.Statements.State.IsFinal%2A>屬性設定為**true**，沒有任何<xref:System.Activities.Statements.State.Exit%2A>活動和轉換源自於此。 若要使用<xref:System.Activities.Core.Presentation.FinalState>活動設計工具加入<xref:System.Activities.Statements.State>預先設定為終止狀態機器狀態的活動拖曳**FinalState**活動設計工具從**狀態機器**區段**工具箱**拖放到工作流程設計工具。 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具可以放到 <xref:System.Activities.Statements.StateMachine> 和稍後加入的轉換，或是可以在放置 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具時建立轉換。 如需有關建立轉換的詳細資訊，請參閱[轉換](../workflow-designer/transition-activity-designer.md)。

### <a name="state-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 State 活動屬性
 下表顯示可使用 <xref:System.Activities.Core.Presentation.FinalState> 設計工具設定的屬性，並說明如何在設計工具中使用它們。 其中一些屬性可以在屬性方格中進行編輯，有些可以在設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.State> 活動設計工具在標頭中的易記名稱。 預設值是**狀態**。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Statements.State.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Statements.State.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.State.Entry%2A>|False|指定此狀態在轉換時發生的動作。 這個值可以拖曳中的活動設定**工具箱**並放到<xref:System.Activities.Statements.State.Entry%2A>區段的狀態。|

## <a name="see-also"></a>另請參閱

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [狀態](../workflow-designer/state-activity-designer.md)
- [轉換](../workflow-designer/transition-activity-designer.md)