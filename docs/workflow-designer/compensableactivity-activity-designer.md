---
title: 工作流程設計工具-CompensableActivity 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4194ef3d4cfbf4b4654b1695c022d715fc7d885
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857917"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 活動設計工具

**CompensableActivity**活動設計工具會用來建立及設定<xref:System.Activities.Statements.CompensableActivity>活動。

## <a name="the-compensableactivity-activity"></a>CompensableActivity 活動
 <xref:System.Activities.Statements.CompensableActivity> 會定義工作的單元，在順利完成之後，可以確認或補償該單元。

### <a name="using-the-compensableactivity-activity-designer"></a>使用 CompensableActivity 活動設計工具
 **CompensableActivity**活動設計工具位於**交易**分類**工具箱**。 若要開啟 **工具箱**，選取**工具箱**工作流程設計工具左側的索引標籤。 或者，選取**工具箱**從**檢視**功能表，或是按下**Ctrl**+**Alt** + **X**。

 **CompensableActivity**活動設計工具可以從拖曳**工具箱**並放到工作流程設計工具介面。 您無法卸除活動設計工具內<xref:System.Activities.Statements.Sequence>。 卸除活動設計工具會建立<xref:System.Activities.Statements.CompensableActivity>預設值的活動<xref:System.Activities.Activity.DisplayName%2A>CompensableActivity。 編輯<xref:System.Activities.Activity.DisplayName%2A>標頭中的值**CompensableActivity**活動設計工具。 它也可以編輯中**DisplayName**屬性方格的方塊。

### <a name="the-compensableactivity-properties"></a>CompensableActivity 屬性
 下表顯示 <xref:System.Activities.Statements.CompensableActivity> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A>和<xref:System.Activities.Activity%601.Result%2A>屬性可以在屬性方格中編輯，但其他屬性必須在工作流程設計工具介面上編輯。

|屬性名稱|必要項|使用方式|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 活動可選用的易記名稱。 預設為 CompensableActivity。|
|<xref:System.Activities.Activity%601.Result%2A>|False|指定 <xref:System.Activities.Statements.CompensableActivity> 的傳回值。 這個屬性必須在屬性方格中編輯。|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|指定提供補償、取消及確認邏輯的活動。 若要新增<xref:System.Activities.Statements.CompensableActivity.Body%2A>活動，從下拉式**工具箱**到**主體**方塊**CompensableActivity**活動設計工具。 加入提示文字 「 在此置放活動 」。|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|指定取消時執行的活動。 若要加入該活動，卸除其設計工具從**工具箱**成**已 CancellationHandler**方塊**CompensableActivity**活動設計工具。 新增提示文字 「 置放活動 」。|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|指定補償 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Compensate> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入該活動，卸除其活動設計工具，從**工具箱**成**CompensationHandler**方塊**CompensableActivity**活動設計工具。 新增提示文字 「 置放活動 」。|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|指定確認 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Confirm> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入該活動，卸除其活動設計工具，從**工具箱**成**Compensationactivity**方塊**CompensableActivity**活動設計工具。 新增提示文字 「 置放活動 」。|

## <a name="see-also"></a>另請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)