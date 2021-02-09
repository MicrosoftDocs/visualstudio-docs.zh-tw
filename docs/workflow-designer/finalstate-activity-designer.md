---
title: 工作流程設計工具 FinalState 活動設計工具
description: 瞭解如何使用 FinalState 設計工具來建立可終止狀態機器實例的狀態。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a6ec51d17453a13f8c3ab1adffc5447afb5db7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894175"
---
# <a name="finalstate-activity-designer"></a>FinalState 活動設計工具

<xref:System.Activities.Core.Presentation.FinalState> 設計工具是用來建立會終止狀態機器執行個體的 <xref:System.Activities.Statements.State>。

## <a name="using-the-finalstate-activity-designer"></a>使用 FinalState 活動設計工具

**FinalState** 設計工具是用來建立在 <xref:System.Activities.Statements.State> 狀態機器中預先設定為終止狀態的。 <xref:System.Activities.Statements.State>使用活動設計工具建立的會 <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State.IsFinal%2A> 將其屬性設定為 **true**，而且沒有任何 <xref:System.Activities.Statements.State.Exit%2A> 活動和來源的轉換。 若要使用 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具 <xref:System.Activities.Statements.State> ，在狀態機器中加入預先設定為終止狀態的活動，請從 [工具箱] 的 [**狀態機器**] 區段中，將 [ **FinalState** ] 活動設計工具拖放到工作流程設計 **工具** 上。 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具可以放到 <xref:System.Activities.Statements.StateMachine> 和稍後加入的轉換，或是可以在放置 <xref:System.Activities.Core.Presentation.FinalState> 活動設計工具時建立轉換。 如需建立轉換的詳細資訊，請參閱 [轉換](../workflow-designer/transition-activity-designer.md)。

### <a name="state-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 State 活動屬性

下表顯示可使用 <xref:System.Activities.Core.Presentation.FinalState> 設計工具設定的屬性，並說明如何在設計工具中使用它們。 其中一些屬性可以在屬性方格中進行編輯，有些可以在設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.State> 活動設計工具在標頭中的易記名稱。 預設值為 [ **狀態**]。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。 <xref:System.Activities.Statements.State.DisplayName%2A> 可用於階層連結巡覽，顯示在工作流程設計工具的頂端。<br /><br /> 雖然 <xref:System.Activities.Statements.State.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.State.Entry%2A>|否|指定此狀態在轉換時發生的動作。 您可以從 [ **工具箱** ] 將活動拖放到狀態的區段，以設定這個值 <xref:System.Activities.Statements.State.Entry%2A> 。|

## <a name="see-also"></a>另請參閱

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [轉換](../workflow-designer/transition-activity-designer.md)