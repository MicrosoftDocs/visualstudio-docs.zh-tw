---
title: 工作流程設計工具-ForEach &lt;T &gt; 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf2f62c482deac963f597c9861fbf2acedc945c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650389"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt;T &gt; 活動設計工具

<xref:System.Activities.Statements.ForEach%601> 活動會針對指定 <xref:System.Activities.Statements.ForEach%601.Body%2A> 集合中的各個項目，執行其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 中包含的活動。

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T \> 工作流程設計工具中的屬性

下表顯示最為實用的 <xref:System.Activities.Statements.ForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> 活動的易記名稱。 預設值為 ForEach < Int32 \>。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|要重複項目的集合。 若要設定 <xref:System.Activities.Statements.ForEach%601.Values%2A>，請在 [ **ForEach < t \>** 活動設計工具] 或屬性方格的 [**值**] 方塊中，輸入 Visual Basic 運算式。|
|*TypeArgument*|True|泛型參數*t*所指定之 <xref:System.Activities.Statements.ForEach%601.Values%2A> 集合中的專案類型。根據預設， *TypeArgument*會設定為**Int32**。 若要變更類型，請在屬性方格中變更 [ *TypeArgument* ] 下拉式方塊的值。|

根據預設，迴圈反覆運算器會命名為**item**。 您可以在 <xref:System.Activities.Statements.ForEach%601> 活動設計工具中變更 Iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>請參閱

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)