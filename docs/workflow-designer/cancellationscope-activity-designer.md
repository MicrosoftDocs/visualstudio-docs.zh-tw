---
title: 工作流程設計工具 CancellationScope 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a2fd36d81f774ca48cca170b8a4a256d73cf1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650707"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活動設計工具

[ **CancellationScope** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.CancellationScope> 活動。

## <a name="the-cancellationscope-activity"></a>CancellationScope 活動

<xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。

### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活動設計工具

[ **CancellationScope** ] 活動設計工具可以在 [**工具箱**] 的 [**交易**] 類別中找到。 若要開啟 **工具箱**，請選取 工作流程設計工具的 **工具箱** 索引標籤。 或者，從  **View**  功能表中選取 **工具箱**，或按**Ctrl** +**Alt** +**X**。

[ **CancellationScope** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 卸載 [ **CancellationScope** ] 活動設計工具會建立具有預設 <xref:System.Activities.Activity.DisplayName%2A> CancellationScope 的 <xref:System.Activities.Statements.CancellationScope> 活動。 在 [ **CancellationScope** ] 活動設計工具的標頭中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。 您也可以在屬性方格的 [ **DisplayName** ] 方塊中編輯它。

### <a name="the-cancellationscope-properties"></a>CancellationScope 屬性

下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 @No__t_0 屬性可以在屬性方格中編輯，但其他屬性必須在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。 預設為 CancellationScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定提供取消邏輯的活動。 若要加入 <xref:System.Activities.Statements.CancellationScope.Body%2A> 活動，請將活動從 [**工具箱**] 拖放至 [ **CancellationScope** ] 活動設計工具上**的 [內**文] 方塊中。 新增提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定在取消時執行的活動。 若要加入 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活動，請將活動從 [工具箱] 拖放到 [ **CancellationScope** ] 活動設計**工具**上的 [ **CancellationHandler** ] 方塊中。 新增提示文字「在此放置活動」。|

## <a name="see-also"></a>請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)