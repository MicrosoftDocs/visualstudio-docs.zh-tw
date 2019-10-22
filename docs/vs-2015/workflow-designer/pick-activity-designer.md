---
title: Pick 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: daefc48cfff2c5c73d9ecf14316777becf4d83c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672602"
---
# <a name="pick-activity-designer"></a>Pick 活動設計工具
<xref:System.Activities.Statements.Pick> 活動會提供以事件為主的控制流程。 活動會執行若干分支的其中一個，以回應觸發的事件。

## <a name="the-pick-activity"></a>Pick 活動
 <xref:System.Activities.Statements.Pick> 活動包含 <xref:System.Activities.Statements.PickBranch> 物件的集合，<xref:System.Activities.Statements.Pick> 活動可因部分做為觸發的傳入事件而執行這些物件中的其中一個。 透過這種方式，[!INCLUDE[wfd1](../includes/wfd1-md.md)] 提供了事件架構的控制流程模型。 每個 <xref:System.Activities.Statements.PickBranch> 都包含了 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 及 <xref:System.Activities.Statements.PickBranch.Action%2A>。 剛開始執行 <xref:System.Activities.Statements.Pick> 活動時，會排程 <xref:System.Activities.Statements.PickBranch> 項目的所有觸發活動。 第一個活動完成時，就會排程對應的動作活動，然後取消其他所有觸發活動。

### <a name="how-to-use-the-pick-activity-designer"></a>如何使用 Pick 活動設計工具
 [ **Pick** ] 活動設計**工具**位於 [工具箱] 的 [**控制流程**] 分類中，若要存取，請按一下 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 上的 [**工具箱**] 索引標籤（也可以從 [**視圖**] 功能表選取 [**工具列**]，或按 CTRL + ALT+ X）。

 [ **Pick** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上通常用來放置活動設計工具的任一處，例如在 [ **Sequence** ] 活動設計工具內。 置放到 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 上後，會建立 <xref:System.Activities.Statements.Pick> 活動，根據預設，此活動會包含兩個空的 <xref:System.Activities.Statements.PickBranch> 活動以做為會顯示 Branch1 和 Branch2 名稱的項目。 這些個別的 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 屬性值可以在 [ **PickBranch** ] 活動設計工具標頭中編輯，或是在每個分支的 [**屬性**] 視窗中編輯。

 有兩種方式可以將 <xref:System.Activities.Statements.PickBranch> 活動加入至 <xref:System.Activities.Statements.Pick> 物件的集合：從 [工具箱] 拖放 [ **PickBranch** ] 設計**工具**，或使用 [**挑選**] 設計介面中的內容功能表。 如需詳細資訊，請參閱[PickBranch](../workflow-designer/pickbranch-activity-designer.md)主題。 請注意，唯一可以放在**Pick**活動設計工具內的專案是**PickBranch**活動設計工具。

### <a name="pick-activity-properties-in-the-workflow-designer"></a>工作流程設計工具中的 Pick 活動屬性
 下表顯示 <xref:System.Activities.Statements.Pick> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中或在設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Pick> 活動設計工具在標頭中的易記名稱。 預設值為 Pick。 此值可在屬性方格中編輯，或是直接在活動設計工具的標頭上編輯。<br /><br /> 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|

## <a name="see-also"></a>請參閱
 [使用 Pick 活動的](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)[控制流程](../workflow-designer/control-flow-activity-designers.md)[挑選活動](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)