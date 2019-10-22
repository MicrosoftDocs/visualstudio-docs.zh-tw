---
title: StateMachine 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660110"
---
# <a name="statemachine-activity-designer"></a>StateMachine 活動設計工具
<xref:System.Activities.Statements.StateMachine> 活動包含狀態和模型工作流程的集合，這些工作流程使用熟悉的狀態機器開發架構。

## <a name="using-the-statemachine-activity-designer"></a>使用 StateMachine 活動設計工具
 若要加入 <xref:System.Activities.Statements.StateMachine> 活動，請從 [工具箱] 的 [**狀態機器**] 區段中，將 [ **StateMachine** ] 活動設計**工具**拖曳至 [[!INCLUDE[wfd1](../includes/wfd1-md.md)]] 介面上。 若要將子狀態新增至此 <xref:System.Activities.Statements.StateMachine> 活動，請從 [**工具箱**] 中拖曳 <xref:System.Activities.Statements.State> 或 <xref:System.Activities.Core.Presentation.FinalState>，然後將它放到**StateMachine**上。

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 StateMachine 活動屬性
 下表顯示可使用工作流程設計工具設定的 <xref:System.Activities.Statements.StateMachine> 屬性，並說明如何在設計工具中使用它們。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.StateMachine> 活動設計工具在標頭中的易記名稱。 預設值為 [ **StateMachine**]。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Activity.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|

## <a name="see-also"></a>請參閱
 [流程圖](../workflow-designer/flowchart-activity-designer.md)[控制流程](../workflow-designer/control-flow-activity-designers.md)