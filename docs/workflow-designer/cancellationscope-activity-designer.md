---
title: CancellationScope 活動設計工具
description: 瞭解如何使用工作流程設計工具中的 [CancellationScope] 活動設計工具來建立和設定 CancellationScope 活動。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef415763a67232f79b269650abecfe6bcabe6bd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937195"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活動設計工具

**CancellationScope** 活動設計工具是用來建立及設定 <xref:System.Activities.Statements.CancellationScope> 活動。

## <a name="the-cancellationscope-activity"></a>CancellationScope 活動

<xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。

### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活動設計工具

[ **CancellationScope** ] 活動設計工具可在 [**工具箱**] 的 [**交易**] 類別中找到。 若要開啟 [ **工具箱**]，請選取工作流程設計工具的 [ **工具箱** ] 索引標籤。 或者，從 [ **View** ] 功能表選取 [**工具箱**]，或按 **Ctrl** + **Alt** + **X**。

[ **CancellationScope** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到工作流程設計工具介面上放置活動的任一處，例如內部 <xref:System.Activities.Statements.Sequence> 。 卸載 **CancellationScope** 活動設計工具 <xref:System.Activities.Statements.CancellationScope> 時，會建立具有預設值 CancellationScope 的活動 <xref:System.Activities.Activity.DisplayName%2A> 。 <xref:System.Activities.Activity.DisplayName%2A>在 [ **CancellationScope** ] 活動設計工具的標頭中編輯值。 您也可以在屬性方格的 [ **DisplayName** ] 方塊中編輯它。

### <a name="the-cancellationscope-properties"></a>CancellationScope 屬性

下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A>屬性可以在屬性方格中編輯，但其他屬性必須在工作流程設計工具介面上編輯。

|屬性名稱|必要|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。 預設為 CancellationScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|是|指定提供取消邏輯的活動。 若要加入 <xref:System.Activities.Statements.CancellationScope.Body%2A> 活動，請從 [工具箱 **] 將** 活動拖放到 [ **CancellationScope** ] 活動設計 **工具** 的 [內文] 方塊中。 新增提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|是|如果有取消，則指定執行的活動。 若要加入 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活動，請從 [工具箱] 將活動拖放到 [ **CancellationScope** ] 活動設計 **工具** 上的 [ **CancellationHandler** ] 方塊中。 新增提示文字「在此放置活動」。|

## <a name="see-also"></a>另請參閱

- [交易](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [確認](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
