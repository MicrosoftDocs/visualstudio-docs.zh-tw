---
title: 工作流程設計工具-CancellationScope 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1032df2f7ebcf4cbc1eae0d4b18757a3f90c4f68
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758053"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活動設計工具

**CancellationScope**活動設計工具會用來建立及設定<xref:System.Activities.Statements.CancellationScope>活動。

## <a name="the-cancellationscope-activity"></a>CancellationScope 活動

<xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。

### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活動設計工具

**CancellationScope**活動設計工具位於**交易**分類**工具箱**。 若要開啟 [**工具箱**，選取**工具箱**的工作流程設計工具] 索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

**CancellationScope**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面，不論用來放置活動，例如內部<xref:System.Activities.Statements.Sequence>。 卸除**CancellationScope**活動設計工具會建立<xref:System.Activities.Statements.CancellationScope>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>CancellationScope。 編輯<xref:System.Activities.Activity.DisplayName%2A>標頭中的值**CancellationScope**活動設計工具。 您也可以編輯它**DisplayName**屬性方格的方塊。

### <a name="the-cancellationscope-properties"></a>CancellationScope 屬性

下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A>屬性可以在屬性方格中編輯，但其他屬性必須在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。 預設為 CancellationScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定提供取消邏輯的活動。 若要新增<xref:System.Activities.Statements.CancellationScope.Body%2A>活動，從下拉式**工具箱**到**主體**方塊**CancellationScope**活動設計工具。 新增提示文字 「 置放活動 」。|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定如果沒有取消執行的活動。 若要新增<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>活動，從下拉式**工具箱**到**已 CancellationHandler**方塊**CancellationScope**活動設計工具。 新增提示文字 「 置放活動 」。|

## <a name="see-also"></a>另請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [補償](../workflow-designer/compensate-activity-designer.md)
- [確認](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)