---
title: 工作流程設計工具-Confirm 活動設計工具
description: 瞭解 Confirm 活動設計工具，以及如何使用這個設計工具來建立和設定確認活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0227a300160434d0052e81d7c1ccd107c5a11a01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955654"
---
# <a name="confirm-activity-designer"></a>Confirm 活動設計工具

[ **Confirm** ] 活動設計工具會用來建立及設定 <xref:System.Activities.Statements.Confirm> 活動。

## <a name="the-confirm-activity"></a>Confirm 活動
 <xref:System.Activities.Statements.Confirm> 活動會明確叫用包含在 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 中之活動的 <xref:System.Activities.Statements.CompensableActivity>。 如果 <xref:System.Activities.Statements.Confirm> 活動沒有在 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 之 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity> 的範圍內使用，您必須指定 <xref:System.Activities.Statements.Confirm.Target%2A> 屬性。

 由 <xref:System.Activities.Statements.CompensationToken> 指定的 <xref:System.Activities.Statements.Compensate.Target%2A> 提供了一個方法，一旦 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 順利完成，即可明確確認或補償 <xref:System.Activities.Statements.CompensableActivity>。

### <a name="using-the-confirm-activity-designer"></a>使用 Confirm 活動設計工具
 [ **Confirm** ] 活動設計工具位於 [**工具箱**] 的 [**交易**] 類別中，若要存取，請按一下工作流程設計工具左側的 [**工具箱**] 索引標籤。 或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

 [ **Confirm** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上通常用來放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.Confirm> 活動，具有 Confirm 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 此 <xref:System.Activities.Activity.DisplayName%2A> 值可以在 [ **確認** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-confirm-properties"></a>Confirm 屬性
 下表顯示 <xref:System.Activities.Statements.Confirm> 屬性，並且描述屬性在設計工具中的使用方式。 屬性 <xref:System.Activities.Activity.DisplayName%2A> 可以在屬性方格中或在工作流程設計工具介面上編輯，但 <xref:System.Activities.Statements.Confirm.Target%2A> 屬性必須在屬性方格中進行編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|指定 <xref:System.Activities.Statements.CancellationScope> 活動選用的易記名稱。 預設為 Confirm。|
|<xref:System.Activities.Statements.Confirm.Target%2A>|是|指定 <xref:System.Activities.InArgument%601>，其中包含此 <xref:System.Activities.Statements.CompensationToken> 活動的 <xref:System.Activities.Statements.Confirm>。|

## <a name="see-also"></a>另請參閱

- [交易](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)