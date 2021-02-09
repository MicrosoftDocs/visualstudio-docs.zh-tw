---
title: 工作流程設計工具-ForEach &lt; T &gt; 活動設計工具
description: 瞭解 ForEach 活動如何 <T> 針對指定值集合中的每個專案，執行其主體中包含的活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c594e613d1160794e8310695d61bcc97902caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876455"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; T &gt; 活動設計工具

<xref:System.Activities.Statements.ForEach%601> 活動會針對指定 <xref:System.Activities.Statements.ForEach%601.Body%2A> 集合中的各個項目，執行其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 中包含的活動。

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach<\> 工作流程設計工具中的 T 屬性

下表顯示最為實用的 <xref:System.Activities.Statements.ForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.ForEach%601> 活動的易記名稱。 預設值為 ForEach<Int32 \> 。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|是|要重複項目的集合。 若要設定 <xref:System.Activities.Statements.ForEach%601.Values%2A> ，請在 **\> ForEach<T** 活動設計工具或在屬性方格的 [**值**] 方塊中，輸入 Visual Basic 運算式。|
|*TypeArgument*|是|<xref:System.Activities.Statements.ForEach%601.Values%2A>泛型參數 *T* 所指定集合中的專案類型。根據預設， *TypeArgument* 設定為 **Int32**。 若要變更類型，請變更屬性方格中 [ *TypeArgument* ] 下拉式方塊的值。|

依預設，迴圈反覆運算器的名稱為 **item**。 您可以在 <xref:System.Activities.Statements.ForEach%601> 活動設計工具中變更 Iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>另請參閱

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)
