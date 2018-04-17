---
title: Compensate 活動設計工具 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef289304338ea64a72c073711a287612d39bd1a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="compensate-activity-designer"></a>Compensate 活動設計工具
**補償**活動設計工具用來建立及設定<xref:System.Activities.Statements.Compensate>活動。

## <a name="the-compensate-activity"></a>Compensate 活動
 <xref:System.Activities.Statements.Compensate> 活動會明確叫用包含在 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 中之活動的 <xref:System.Activities.Statements.CompensableActivity>。 如果 <xref:System.Activities.Statements.Compensate> 活動沒有在 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 之 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 或 <xref:System.Activities.Statements.CompensableActivity> 的範圍內使用，您必須指定 <xref:System.Activities.Statements.Compensate.Target%2A> 屬性。

 由 <xref:System.Activities.Statements.CompensationToken> 指定的 <xref:System.Activities.Statements.Compensate.Target%2A> 提供了一個方法，一旦 <xref:System.Activities.Statements.CompensableActivity> 的 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 順利完成，即可明確確認或補償 <xref:System.Activities.Statements.CompensableActivity>。

### <a name="using-the-compensate-activity-designer"></a>使用 Compensate 活動設計工具
 **補償**活動設計工具位於**交易**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左半部[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **補償**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.Compensate> 活動，具有 Compensate 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**補償**活動設計工具或在**DisplayName**屬性方格的方塊。

### <a name="the-compensate-properties"></a>Compensate 屬性
 下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中或在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯，但 <xref:System.Activities.Statements.Compensate.Target%2A> 屬性必須在屬性方格中編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|指定 <xref:System.Activities.Statements.Compensate> 活動選用的易記名稱。 預設為 Compensate。|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|指定 <xref:System.Activities.InArgument%601>，其中包含此 <xref:System.Activities.Statements.CompensationToken> 活動的 <xref:System.Activities.Statements.Compensate>。|

## <a name="see-also"></a>另請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate 活動設計工具](../workflow-designer/compensate-activity-designer.md)
- [確認](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)