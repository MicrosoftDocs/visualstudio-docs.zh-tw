---
title: 工作流程設計工具-Compensate 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7c195c9bfd6bedf0220a989c31936975fb6d70a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950425"
---
# <a name="compensate-activity-designer"></a>Compensate 活動設計工具

**補償**活動設計工具會用來建立及設定<xref:System.Activities.Statements.Compensate>活動。

## <a name="the-compensate-activity"></a>Compensate 活動

<xref:System.Activities.Statements.Compensate> 活動會明確叫用包含在 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中之活動的 <xref:System.Activities.Statements.CompensableActivity>。 如果 <xref:System.Activities.Statements.Compensate> 活動沒有在 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 之 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity> 的範圍內使用，您必須指定 <xref:System.Activities.Statements.Compensate.Target%2A> 屬性。

由 <xref:System.Activities.Statements.CompensationToken> 指定的 <xref:System.Activities.Statements.Compensate.Target%2A> 提供了一個方法，一旦 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 順利完成，即可明確確認或補償 <xref:System.Activities.Statements.CompensableActivity>。

### <a name="using-the-compensate-activity-designer"></a>使用 Compensate 活動設計工具

**補償**活動設計工具位於**交易**分類**工具箱**。 若要開啟 **工具箱**，選取**工具箱**工作流程設計工具左側的索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**補償**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論用來放置活動，例如內部<xref:System.Activities.Statements.Sequence>。 卸除活動設計工具會建立<xref:System.Activities.Statements.Compensate>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>的補償。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**補償**活動設計工具或**DisplayName**屬性方格的方塊。

### <a name="the-compensate-properties"></a>Compensate 屬性

下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A>屬性也可以在屬性方格中或在工作流程設計工具介面上編輯。 編輯<xref:System.Activities.Statements.Compensate.Target%2A>屬性方格中的屬性。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Compensate> 活動選用的易記名稱。 預設為 Compensate。|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，其中包含此 <xref:System.Activities.Statements.CompensationToken> 活動的 <xref:System.Activities.Statements.Compensate>。|

## <a name="see-also"></a>另請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate 活動設計工具](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)