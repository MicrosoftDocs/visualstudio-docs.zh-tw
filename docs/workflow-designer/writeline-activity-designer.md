---
title: 工作流程設計工具-WriteLine 活動設計工具
description: 瞭解 [WriteLine] 活動，以及如何使用 [WriteLine] 活動設計工具來建立和設定 [WriteLine] 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cb4806949b21a6c92548b91623e63306f2a7722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875103"
---
# <a name="writeline-activity-designer"></a>WriteLine 活動設計工具

[ **WriteLine** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.WriteLine> 活動。

## <a name="the-writeline-activity"></a>WriteLine 活動。

<xref:System.Activities.Statements.WriteLine> 活動會將文字寫入至指定的 <xref:System.IO.TextWriter> 物件。 如果未指定任何 <xref:System.IO.TextWriter>，<xref:System.Activities.Statements.WriteLine> 就會將文字寫入至主控台。

### <a name="using-the-writeline-activity-designer"></a>使用 WriteLine 活動設計工具

在 [工具箱] 的 [**基本**] 類別中存取 [ **WriteLine** ] 活動設計 **工具**。 [ **WriteLine** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.WriteLine> 活動，具有 WriteLine 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以在 [ **WriteLine** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-writeline-properties"></a>WriteLine 屬性

下表顯示 <xref:System.Activities.Statements.WriteLine> 屬性，並且描述屬性在設計工具中的使用方式。 這些屬性可以在屬性方格中進行編輯，其中有一些可以在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.WriteLine> 活動的易記名稱。 預設值為 WriteLine。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|否|要寫入的文字。 若要設定屬性，請在 [ **WriteLine** ] 活動設計工具的 **文字方塊** 中或在屬性方格中輸入 Visual Basic 運算式。|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|否|<xref:System.IO.TextWriter> 從中寫入 <xref:System.Activities.Statements.WriteLine> 的 <xref:System.Activities.Statements.WriteLine.Text%2A>。 預設值為主控台。|

## <a name="see-also"></a>另請參閱

- [基本](../workflow-designer/primitives-activity-designers.md)
- [指派](../workflow-designer/assign-activity-designer.md)
- [延遲](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
