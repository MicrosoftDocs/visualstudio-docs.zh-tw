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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656999"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 活動設計工具
**CompensableActivity**活動設計工具是用來建立及設定 <xref:System.Activities.Statements.CompensableActivity> 活動。

## <a name="the-compensableactivity-activity"></a>CompensableActivity 活動
 <xref:System.Activities.Statements.CompensableActivity> 會定義工作的單元，在順利完成之後，可以確認或補償該單元。

### <a name="using-the-compensableactivity-activity-designer"></a>使用 CompensableActivity 活動設計工具
 [ **CompensableActivity** ] 活動設計工具位於 [**工具箱**] 的 [**交易**] 類別中，若要存取，請按一下 (左側的 [**工具箱**] 索引標籤， [!INCLUDE[wfd2](../includes/wfd2-md.md)] 也可以從 [ **VIEW** ] 功能表選取 [**工具列**]，或按 CTRL + ALT + X。 ) 

 [ **CompensableActivity** ] 活動設計工具可以從 [ **工具箱** ] 拖曳出來，放到介面上通常用來放置活動的任一處 [!INCLUDE[wfd2](../includes/wfd2-md.md)] ，例如內部 <xref:System.Activities.Statements.Sequence> 。 這會建立一個 <xref:System.Activities.Statements.CompensableActivity> 活動，具有 CompensableActivity 的預設 <xref:System.Activities.Activity.DisplayName%2A>。 <xref:System.Activities.Activity.DisplayName%2A>值可以在 [ **CompensableActivity** ] 活動設計工具的標頭中編輯，或是在屬性方格的 [ **DisplayName** ] 方塊中編輯。

### <a name="the-compensableactivity-properties"></a>CompensableActivity 屬性
 下表顯示 <xref:System.Activities.Statements.CompensableActivity> 屬性，並且描述屬性在設計工具中的使用方式。 <xref:System.Activities.Activity.DisplayName%2A> 與 <xref:System.Activities.Activity%601.Result%2A> 屬性可以在屬性方格中編輯，但其他屬性必須在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 介面上編輯。

|屬性名稱|必要|使用方式|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|否|<xref:System.Activities.Statements.CompensableActivity> 活動可選用的易記名稱。 預設為 CompensableActivity。|
|<xref:System.Activities.Activity%601.Result%2A>|否|指定 <xref:System.Activities.Statements.CompensableActivity> 的傳回值。 這個屬性必須在屬性方格中編輯。|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|是|指定提供補償、取消及確認邏輯的活動。 若要加入 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動，請從 [工具箱 **] 將**活動拖放到 [ **CompensableActivity** ] 活動設計**工具**的 [內文] 方塊中，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|否|指定如果取消時所要執行的活動。 若要加入活動，請將其設計工具從 [工具箱] 拖放到 [ **CompensableActivity** ] 活動設計**工具**上的 [ **CancellationHandler** ] 方塊，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|否|指定補償 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Compensate> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入活動，請將其活動設計工具從 [工具箱] 拖放到 [ **CompensableActivity** ] 活動設計**工具**的 [ **CompensationHandler** ] 方塊中，並在 [在此放置活動] 提示文字。|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|否|指定確認 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 活動時所要執行的活動。 使用 <xref:System.Activities.Statements.Confirm> 活動可以明確叫用這個處理常式。<br /><br /> 若要加入活動，請將其活動設計工具從 [工具箱] 拖放到 [ **CompensableActivity** ] 活動設計**工具**的 [ **ConfirmationHandler** ] 方塊中，並在 [在此放置活動] 提示文字。|

## <a name="see-also"></a>另請參閱
 [交易](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [補償](../workflow-designer/compensate-activity-designer.md)[確認](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)