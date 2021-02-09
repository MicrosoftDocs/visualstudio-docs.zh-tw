---
title: 工作流程設計工具-If 活動設計工具
description: 瞭解 If 活動如何評估條件，並根據該評估的結果執行活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93f36a3c2b587718fe6889688baa50224f663c1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881356"
---
# <a name="if-activity-designer"></a>If 活動設計工具

<xref:System.Activities.Statements.If> 活動會評估條件，並且根據該評估的結果執行某個活動。 這個活動最適合用於使用程式設計的程序模型樣式時。 例如，<xref:System.Activities.Statements.If> 活動可巢狀置入 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Parallel> 活動內部。 如果您要使用 <xref:System.Activities.Statements.Flowchart> 活動，可以考慮改用 <xref:System.Activities.Statements.FlowDecision> 活動。

## <a name="if-properties-in-the-workflow-designer"></a>工作流程設計工具中的 If 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.If> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|是|判斷要執行哪個子活動的條件。 若要設定 <xref:System.Activities.Statements.If.Condition%2A> ，請在 [ **If** ] 活動設計工具上或在屬性方格的 [**條件**] 方塊中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.If.Else%2A>|否|如果為 false 時要執行的活動 <xref:System.Activities.Statements.If.Condition%2A> 。  若要加入由分支執行的活動 <xref:System.Activities.Statements.If.Else%2A> ，請從 [工具箱] 將活動拖放到 [ **If** ] 活動設計 **工具** 上的 [ **Else** ] 方塊，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.If.Then%2A>|否|當為 true 時要執行的活動 <xref:System.Activities.Statements.If.Condition%2A> 。  若要加入由分支執行的活動 <xref:System.Activities.Statements.If.Then%2A> ，請從 [工具箱] 將活動拖放到 [ **If** ] 活動設計 **工具** 上的 [ **Then** ] 方塊，並在 [在此放置活動] 提示文字。|

## <a name="see-also"></a>另請參閱

- [序列](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)
