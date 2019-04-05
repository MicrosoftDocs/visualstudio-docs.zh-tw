---
title: CompensableActivity 活動設計工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f11743e0027866fd45687f716f1989e98020c68e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943963"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 活動設計工具
**CompensableActivity**活動設計工具會用來建立及設定<xref:System.Activities.Statements.CompensableActivity>活動。  
  
## <a name="the-compensableactivity-activity"></a>CompensableActivity 活動  
 <xref:System.Activities.Statements.CompensableActivity> 會定義工作的單元，在順利完成之後，可以確認或補償該單元。  
  
### <a name="using-the-compensableactivity-activity-designer"></a>使用 CompensableActivity 活動設計工具  
 **CompensableActivity**活動設計工具位於**交易**類別**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左側[!INCLUDE[wfd2](../includes/wfd2-md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)  
  
 **CompensableActivity**活動設計工具可以從拖曳**工具箱**，放入[!INCLUDE[wfd2](../includes/wfd2-md.md)]介面只要活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.CompensableActivity> 活動，具有 CompensableActivity 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>可以編輯的標頭中的值**CompensableActivity**活動設計工具或**DisplayName**屬性方格的方塊。  
  
### <a name="the-compensableactivity-properties"></a>CompensableActivity 屬性  
 下表顯示 <xref:System.Activities.Statements.CompensableActivity> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 與 <xref:System.Activities.Activity%601.Result%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。  
  
|屬性名稱|必要|使用量|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 活動可選用的易記名稱。 預設為 CompensableActivity。|  
|<xref:System.Activities.Activity%601.Result%2A>|False|指定 <xref:System.Activities.Statements.CompensableActivity> 的傳回值。 這個屬性必須在屬性方格中編輯。|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|指定提供補償、取消及確認邏輯的活動。 若要新增<xref:System.Activities.Statements.CompensableActivity.Body%2A>活動，從下拉式**工具箱**到**主體**方塊**CompensableActivity**活動設計工具提示文字 「 卸除與活動 」。|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|指定如果取消時所要執行的活動。 若要加入該活動，卸除其設計工具從**工具箱**成**已 CancellationHandler**方塊**CompensableActivity**活動設計工具提示文字 「 卸除與活動 」。|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|指定補償 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Compensate> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入該活動，卸除其活動設計工具，從**工具箱**成**CompensationHandler**方塊**CompensableActivity**活動設計工具提示文字與"在此放置活動 」。|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|指定確認 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Confirm> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入該活動，卸除其活動設計工具，從**工具箱**成**Compensationactivity**方塊**CompensableActivity**活動設計工具提示文字與"在此放置活動 」。|  
  
## <a name="see-also"></a>另請參閱  
 [交易](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [補償](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)