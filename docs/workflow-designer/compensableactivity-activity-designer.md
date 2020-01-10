---
title: 工作流程設計工具 CompensableActivity 活動設計工具
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597096"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 活動設計工具

[ **CompensableActivity** ] 活動設計工具會用來建立和設定 <xref:System.Activities.Statements.CompensableActivity> 活動。

## <a name="the-compensableactivity-activity"></a>CompensableActivity 活動
 <xref:System.Activities.Statements.CompensableActivity> 會定義工作的單元，在順利完成之後，可以確認或補償該單元。

### <a name="using-the-compensableactivity-activity-designer"></a>使用 CompensableActivity 活動設計工具
 [ **CompensableActivity** ] 活動設計工具可以在 [**工具箱**] 的 [**交易**] 類別中找到。 若要開啟 [**工具箱**]，請選取工作流程設計工具左側的 [**工具箱**] 索引標籤。 或者，從  **View**  功能表中選取 **工具箱**，或按**Ctrl**+**Alt**+**X**。

 [ **CompensableActivity** ] 活動設計工具可以從 [**工具箱**] 拖曳出來，放到工作流程設計工具介面上。 您可以將活動設計工具放在 <xref:System.Activities.Statements.Sequence>中。 卸載活動設計工具會建立具有預設 <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity 的 <xref:System.Activities.Statements.CompensableActivity> 活動。 在 [ **CompensableActivity** ] 活動設計工具的標頭中編輯 <xref:System.Activities.Activity.DisplayName%2A> 值。 您也可以在屬性方格的 [ **DisplayName** ] 方塊中編輯它。

### <a name="the-compensableactivity-properties"></a>CompensableActivity 屬性
 下表顯示 <xref:System.Activities.Statements.CompensableActivity> 屬性，並且描述屬性在設計工具中的使用方式。 [<xref:System.Activities.Activity.DisplayName%2A>] 和 [<xref:System.Activities.Activity%601.Result%2A>] 屬性可以在屬性方格中編輯，但其他屬性則必須在工作流程設計工具介面上編輯。

|內容名稱|必要|使用|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 活動可選用的易記名稱。 預設為 CompensableActivity。|
|<xref:System.Activities.Activity%601.Result%2A>|False|指定 <xref:System.Activities.Statements.CompensableActivity> 的傳回值。 這個屬性必須在屬性方格中編輯。|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|指定提供補償、取消及確認邏輯的活動。 若要加入 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動，請將活動從 [**工具箱**] 拖放至 [ **CompensableActivity** ] 活動設計工具上**的 [內**文] 方塊中。 新增提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|指定當有取消時所執行的活動。 若要加入活動，請將其設計**工具**從 [工具箱] 拖放到 [ **CompensableActivity** ] 活動設計工具上的 [ **CancellationHandler** ] 方塊 新增提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|指定補償 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Compensate> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入活動，請將其活動設計**工具**從 [工具箱] 拖放到 [ **CompensableActivity** ] 活動設計工具的 [ **CompensationHandler** ] 方塊中。 新增提示文字「在此放置活動」。|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|指定確認 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Confirm> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入活動，請將其活動設計**工具**從 [工具箱] 拖放到 [ **CompensableActivity** ] 活動設計工具的 [ **ConfirmationHandler** ] 方塊中。 新增提示文字「在此放置活動」。|

## <a name="see-also"></a>請參閱

- [異動](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
