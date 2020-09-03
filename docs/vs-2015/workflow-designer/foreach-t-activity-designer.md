---
title: ForEach &lt; T &gt; 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656660"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; T &gt; 活動設計工具
<xref:System.Activities.Statements.ForEach%601> 活動會針對指定 <xref:System.Activities.Statements.ForEach%601.Body%2A> 集合中的各個項目，執行其 <xref:System.Activities.Statements.ForEach%601.Values%2A> 中包含的活動。

## <a name="foreacht-properties-in-the-workflow-designer"></a>\<T>工作流程設計工具中的 ForEach 屬性
 下表顯示最為實用的 <xref:System.Activities.Statements.ForEach%601> 活動屬性，並且說明它們在設計工具中的使用方式。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.ForEach%601> 活動的易記名稱。 預設值為 ForEach \<Int32> 。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|是|要重複項目的集合。 若要設定 <xref:System.Activities.Statements.ForEach%601.Values%2A> ，請 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 在 [ **ForEach \<T> ** ] 活動設計工具的 [**值**] 方塊或在屬性方格中輸入運算式。|
|*TypeArgument*|是|<xref:System.Activities.Statements.ForEach%601.Values%2A>泛型參數*T*所指定集合中的專案類型。根據預設， *TypeArgument*設定為**Int32**。 若要變更類型，請變更屬性方格中 [ *TypeArgument* ] 下拉式方塊的值。|

 依預設，迴圈反覆運算器的名稱為 **item**。 您可以在 <xref:System.Activities.Statements.ForEach%601> 活動設計工具中變更 Iterator 變數的名稱。 迴圈 Iterator 可用在 <xref:System.Activities.Statements.ForEach%601> 活動子系中的運算式。

## <a name="see-also"></a>另請參閱
 [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md)[控制流程](../workflow-designer/control-flow-activity-designers.md)