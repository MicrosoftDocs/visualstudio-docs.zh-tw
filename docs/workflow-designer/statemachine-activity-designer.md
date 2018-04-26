---
title: 工作流程設計工具-StateMachine 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6a9860d4c6025e6d77a869573b133c6a034aff96
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="statemachine-activity-designer"></a>StateMachine 活動設計工具

<xref:System.Activities.Statements.StateMachine> 活動包含狀態和模型工作流程的集合，這些工作流程使用熟悉的狀態機器開發架構。

## <a name="using-the-statemachine-activity-designer"></a>使用 StateMachine 活動設計工具

若要加入<xref:System.Activities.Statements.StateMachine>活動，拖曳**StateMachine**活動設計工具，從**狀態機器**區段**工具箱**並將它放入 Windows 工作流程設計工具介面。 若要加入至這個子狀態<xref:System.Activities.Statements.StateMachine>活動，拖曳<xref:System.Activities.Statements.State>或<xref:System.Activities.Core.Presentation.FinalState>從**工具箱**並將其放置**StateMachine**。

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 StateMachine 活動屬性

下表顯示可使用工作流程設計工具設定的 <xref:System.Activities.Statements.StateMachine> 屬性，並說明如何在設計工具中使用它們。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.StateMachine> 活動設計工具在標頭中的易記名稱。 預設值是**StateMachine**。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Activity.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|

## <a name="see-also"></a>另請參閱

- [流程圖](../workflow-designer/flowchart-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)