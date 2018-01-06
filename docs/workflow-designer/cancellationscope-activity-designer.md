---
title: "CancellationScope 活動設計工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c6e9206eff3eaaeb3b5a79bb8457738c21af05c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 活動設計工具
**CancellationScope**活動設計工具用來建立及設定<xref:System.Activities.Statements.CancellationScope>活動。  
  
## <a name="the-cancellationscope-activity"></a>CancellationScope 活動  
 <xref:System.Activities.Statements.CancellationScope> 活動可讓您指定執行的活動與該活動的取消邏輯。  
  
### <a name="using-the-cancellationscope-activity-designer"></a>使用 CancellationScope 活動設計工具  
 **CancellationScope**活動設計工具位於**交易**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **CancellationScope**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.CancellationScope> 活動，具有 CancellationScope 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**CancellationScope**活動設計工具或在**DisplayName**屬性方格的方塊。  
  
### <a name="the-cancellationscope-properties"></a>CancellationScope 屬性  
 下表顯示 <xref:System.Activities.Statements.CancellationScope> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。  
  
|屬性名稱|必要項|使用方式|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 活動可選用的易記名稱。 預設為 CancellationScope。 雖然 <xref:System.Activities.Activity.DisplayName%2A> 值並非絕對必要，但建議您盡量使用。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|指定提供取消邏輯的活動。 若要加入<xref:System.Activities.Statements.CancellationScope.Body%2A>活動，請從活動**工具箱**到**主體**方塊上**CancellationScope**活動設計工具的提示文字 「 卸除活動 」。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|指定如果取消時所要執行的活動。 若要加入<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>活動，請從活動**工具箱**到**CancellationHandler**方塊**CancellationScope**活動設計工具的提示「 置放活動 」 文字。|  
  
## <a name="see-also"></a>請參閱  
 [交易](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [補償](../workflow-designer/compensate-activity-designer.md)   
 [確認](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)