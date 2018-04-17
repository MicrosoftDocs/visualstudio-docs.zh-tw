---
title: CompensableActivity 活動設計工具 |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8f9fcf62b727ef3c8b607b503b3305508921e30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 活動設計工具
**CompensableActivity**活動設計工具用來建立及設定<xref:System.Activities.Statements.CompensableActivity>活動。

## <a name="the-compensableactivity-activity"></a>CompensableActivity 活動
 <xref:System.Activities.Statements.CompensableActivity> 會定義工作的單元，在順利完成之後，可以確認或補償該單元。

### <a name="using-the-compensableactivity-activity-designer"></a>使用 CompensableActivity 活動設計工具
 **CompensableActivity**活動設計工具位於**交易**分類**工具箱**，即可存取的哪一個**工具箱**  索引標籤上的左半部[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)](或者，選取**工具列**從**檢視**功能表或 CTRL + ALT + X。)

 **CompensableActivity**活動設計工具可以從拖曳**工具箱**，置放到上[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]介面任一處活動通常放置的例如內部<xref:System.Activities.Statements.Sequence>。 這會建立一個 <xref:System.Activities.Statements.CompensableActivity> 活動，具有 CompensableActivity 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以編輯的標頭中**CompensableActivity**活動設計工具或在**DisplayName**屬性方格的方塊。

### <a name="the-compensableactivity-properties"></a>CompensableActivity 屬性
 下表顯示 <xref:System.Activities.Statements.CompensableActivity> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 與 <xref:System.Activities.Activity%601.Result%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 介面上編輯。

|屬性名稱|必要項|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 活動可選用的易記名稱。 預設為 CompensableActivity。|
|<xref:System.Activities.Activity%601.Result%2A>|False|指定 <xref:System.Activities.Statements.CompensableActivity> 的傳回值。 這個屬性必須在屬性方格中編輯。|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|指定提供補償、取消及確認邏輯的活動。 若要加入<xref:System.Activities.Statements.CompensableActivity.Body%2A>活動，請從活動**工具箱**到**主體**方塊上**CompensableActivity**活動設計工具的提示文字 「 卸除活動 」。|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|指定如果取消時所要執行的活動。 若要加入該活動，卸除其設計工具從**工具箱**到**CancellationHandler**方塊**CompensableActivity**活動設計工具的提示文字 「 拖放活動 」。|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|指定補償 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Compensate> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入該活動，卸除其活動設計工具從**工具箱**到**CompensationHandler**方塊**CompensableActivity**活動設計工具的提示文字 「在此置放活動 」。|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|指定確認 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Confirm> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入該活動，卸除其活動設計工具從**工具箱**到**Compensableactivity**方塊**CompensableActivity**活動設計工具的提示文字 「在此置放活動 」。|

## <a name="see-also"></a>另請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [補償](../workflow-designer/compensate-activity-designer.md)
- [確認](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)