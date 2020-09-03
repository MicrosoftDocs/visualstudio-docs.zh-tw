---
title: CancellationScope 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659171"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活動設計工具
**CancellationScope**活動設計工具是用來建立及設定 <xref:System.Activities.Statements.CancellationScope> 活動。

## <a name="the-cancellationscope-activity"></a>CancellationScope 活動
 <xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。

### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活動設計工具
 [ **CancellationScope** ] 活動設計工具位於 [**工具箱**] 的 [**交易**] 類別中，若要存取，請按一下 (的 [**工具箱**] 索引標籤，也可以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **CancellationScope** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.CancellationScope> 活動，具有 CancellationScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以在 [ **CancellationScope** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-cancellationscope-properties"></a>CancellationScope 屬性
 下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。 預設為 CancellationScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|是|指定提供取消邏輯的活動。 若要加入 <xref:System.Activities.Statements.CancellationScope.Body%2A> 活動，請從 [工具箱 **] 將**活動拖放到 [ **CancellationScope** ] 活動設計**工具**的 [內文] 方塊中，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|是|指定如果取消時所要執行的活動。 若要加入 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活動，請從 [**工具箱**] 將活動拖放到 [ **CancellationScope** ] 活動設計工具上的 [ **CancellationHandler** ] 方塊中，並在 [在此放置活動] 提示文字。|

## <a name="see-also"></a>另請參閱
 [交易](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [補償](../workflow-designer/compensate-activity-designer.md)[確認](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)