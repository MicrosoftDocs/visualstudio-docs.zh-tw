---
title: 工作流程設計工具-ForEach&lt;T&gt;活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d506be0fbee9ad94e4ed8b97665665bc045ed130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970435"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt;活動設計工具

<xref:System.Activities.Statements.ForEach%601> 活動會針對指定 <xref:System.Activities.Statements.ForEach%601.Body%2A> 集合中的各個項目，執行其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 中包含的活動。

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\>工作流程設計工具中的屬性

下表顯示最為實用的 <xref:System.Activities.Statements.ForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> 活動的易記名稱。 預設值是 ForEach < Int32\>。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|要重複項目的集合。 若要設定<xref:System.Activities.Statements.ForEach%601.Values%2A>，輸入在 Visual Basic 運算式**值**方塊**ForEach < T\>** 活動設計工具，或在屬性方格中。|
|*TypeArgument*|True|中的項目類型<xref:System.Activities.Statements.ForEach%601.Values%2A>泛型參數所指定集合*T*。根據預設， *TypeArgument*設**Int32**。 若要變更的類型，將變更的值*TypeArgument*屬性方格中的下拉式方塊。|

根據預設，迴圈 iterator 會命名為**項目**。 您可以在 <xref:System.Activities.Statements.ForEach%601> 活動設計工具中變更 Iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>另請參閱

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [控制流程](../workflow-designer/control-flow-activity-designers.md)