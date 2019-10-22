---
title: 工作流程設計工具-補償活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65203663214e6bc82a4a7b20af9caa25bfd98ee4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650659"
---
# <a name="compensate-activity-designer"></a>Compensate 活動設計工具

[**補償**] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.Compensate> 活動。

## <a name="the-compensate-activity"></a>Compensate 活動

<xref:System.Activities.Statements.Compensate> 活動會明確叫用包含在 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中之活動的 <xref:System.Activities.Statements.CompensableActivity>。 如果 <xref:System.Activities.Statements.Compensate> 活動沒有在 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 之 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity> 的範圍內使用，您必須指定 <xref:System.Activities.Statements.Compensate.Target%2A> 屬性。

由 <xref:System.Activities.Statements.CompensationToken> 指定的 <xref:System.Activities.Statements.Compensate.Target%2A> 提供了一個方法，一旦 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 順利完成，即可明確確認或補償 <xref:System.Activities.Statements.CompensableActivity>。

### <a name="using-the-compensate-activity-designer"></a>使用 Compensate 活動設計工具

[**補償**] 活動設計工具可以在 [**工具箱**] 的 [**交易**] 類別中找到。 若要開啟 [**工具箱**]，請選取工作流程設計工具左側的 [**工具箱**] 索引標籤。 或者，從  **View**  功能表中選取 **工具箱**，或按**Ctrl** +**Alt** +**X**。

[**補償**] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上放置活動的任一處，例如在 <xref:System.Activities.Statements.Sequence> 內部。 卸載活動設計工具會建立具有預設 <xref:System.Activities.Activity.DisplayName%2A> 補償的 <xref:System.Activities.Statements.Compensate> 活動。 您可以在 [**補償**] 活動設計工具的標頭中，或在屬性方格的 [ **DisplayName** ] 方塊中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。

### <a name="the-compensate-properties"></a>Compensate 屬性

下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 @No__t_0 屬性可以在屬性方格中或在工作流程設計工具介面上編輯。 編輯屬性方格中的 [<xref:System.Activities.Statements.Compensate.Target%2A>] 屬性。

|屬性名稱|必要項|使用量|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Compensate> 活動選用的易記名稱。 預設為 Compensate。|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，其中包含此 <xref:System.Activities.Statements.CompensationToken> 活動的 <xref:System.Activities.Statements.Compensate>。|

## <a name="see-also"></a>請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate 活動設計工具](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)