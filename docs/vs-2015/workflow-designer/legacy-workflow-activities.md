---
title: 舊版工作流程活動 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302953"
---
# <a name="legacy-workflow-activities"></a>舊版工作流程活動
[!INCLUDE[wf](../includes/wf-md.md)] 包含一組預設的活動，可提供控制流程、條件、事件處理、狀態管理，以及與應用程式和服務進行通訊的功能。 設計工作流程時，您可以使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 系統提供的活動，或者建立自訂活動。

 下表列出 [!INCLUDE[wf2](../includes/wf2-md.md)] 架構全新的活動集。 許多 (但非全部) 活動都是由活動設計工具所表示，這些工具可以從  **的 [** 工具箱[!INCLUDE[wfd2](../includes/wfd2-md.md)]] 存取。 若要建立活動，請將它的設計工具從 [**工具箱**] 拖放到設計介面上。

|活動|描述|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|與**HandleExternalEventActivity**活動搭配使用，以進行與本機服務的輸入和輸出通訊。 [使用 CallExternalMethodActivity 活動](https://go.microsoft.com/fwlink?LinkID=65060)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|用於包含清除邏輯，適用於複合活動的所有子系完成執行前即取消複合活動時。 [使用 CancellationHandlerActivity 活動](https://go.microsoft.com/fwlink?LinkID=65061)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|讓您將 Visual Basic 或 C# 程式碼新增至您的工作流程。 [使用 CodeActivity 活動](https://go.microsoft.com/fwlink?LinkID=65062)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)的可補償版本。 [使用 CompensatableSequenceActivity 活動](https://go.microsoft.com/fwlink?LinkID=65002)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|**TransactionScopeActivity**的可補償版本。 [使用 CompensatableTransactionScopeActivity 活動](https://go.microsoft.com/fwlink?LinkID=65063)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|當錯誤發生時，可讓您呼叫程式碼以復原或補償工作流程已執行的作業。 [使用 CompensateActivity 活動](https://go.microsoft.com/fwlink?LinkID=65064)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|一或多個活動的包裝函式，可針對已完成的 TransactionScopeActivity 活動執行補償，[!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensationHandlerActivity 活動](https://go.microsoft.com/fwlink?LinkID=65065)。|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|根據適用于[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)活動本身的條件，以及根據個別套用至每個子系的條件，來執行子活動。 [使用 ConditionedActivityGroup 活動](https://go.microsoft.com/fwlink?LinkID=65066)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|可讓您在工作流程中建置以逾時間隔為基礎的延遲。 [使用 DelayActivity 活動](https://go.microsoft.com/fwlink?LinkID=65067)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|包裝一或多個發生指定事件時執行的活動。 [使用 EventDrivenActivity 活動](https://go.microsoft.com/fwlink?LinkID=65068)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|提供將事件與活動產生關聯的架構。 [使用 EventHandlersActivity 活動](https://go.microsoft.com/fwlink?LinkID=65069)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|同時執行其主要子活動與[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)。 [使用 EventHandlingScopeActivity 活動](https://go.microsoft.com/fwlink?LinkID=65070)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|用於處理您指定之類型的例外狀況。 [使用 FaultHandlerActivity 活動](https://go.microsoft.com/fwlink?LinkID=65071)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|代表具有[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)類型子活動之已排序清單的複合活動。 [使用 FaultHandlersActivity 活動](https://go.microsoft.com/fwlink?LinkID=65072)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|與[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)活動搭配使用，以進行與本機服務的輸入和輸出通訊。 [使用 HandleExternalEventActivity 活動](https://go.microsoft.com/fwlink?LinkID=65073)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|測試每個分支上的條件，並在條件等於**true**的第一個分支上執行活動。 [使用 IfElseActivity 活動](https://go.microsoft.com/fwlink?LinkID=65074)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|表示[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)的分支。 [使用 IfElseBranchActivity 活動](https://go.microsoft.com/fwlink?LinkID=65075)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|可讓您的工作流程叫用 Web 服務。 [使用 InvokeWebServiceActivity 活動](https://go.microsoft.com/fwlink?LinkID=65076)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|可讓您的工作流程叫用另一個工作流程。 [使用 InvokeWorkflowActivity 活動](https://go.microsoft.com/fwlink?LinkID=65077)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|只包含[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)子活動的複合活動。 [使用 ListenActivity 活動](https://go.microsoft.com/fwlink?LinkID=65078)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|提供一種方式，可將兩個或多個子**SequenceActivity**活動分支排程在同一時間進行處理。 [使用 ParallelActivity 活動](https://go.microsoft.com/fwlink?LinkID=65079)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|用來表示規則的集合。 規則，其中包含條件和結果動作。 [使用 PolicyActivity 活動](https://go.microsoft.com/fwlink?LinkID=65004)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|建立單一子活動的多個執行個體。 [使用 ReplicatorActivity 活動](https://go.microsoft.com/fwlink?LinkID=65080)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|提供一種簡單的方法將多個活動連結在一起，以進行循序執行。 [使用 SequenceActivity 活動](https://go.microsoft.com/fwlink?LinkID=65081)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|指定轉換至新狀態。 [使用 SetStateActivity 活動](https://go.microsoft.com/fwlink?LinkID=65082)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|表示狀態機器工作流程中的狀態。 [使用 StateActivity 活動](https://go.microsoft.com/fwlink?LinkID=65083)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|用於[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)活動中，做為離開**StateActivity**活動時所執行子活動的容器。 [使用 StateFinalizationActivity 活動](https://go.microsoft.com/fwlink?LinkID=65008)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|在[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)活動中用來作為輸入**StateActivity**活動時所執行子活動的容器。 [使用 StateInitializationActivity 活動](https://go.microsoft.com/fwlink?LinkID=65006)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|暫止工作流程的作業，以便在有某些需要特別注意的錯誤狀況時介入。 [使用 SuspendActivity 活動](https://go.microsoft.com/fwlink?LinkID=65084)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|在同步化領域中循序執行所包含的活動。 [使用 SynchronizationScopeActivity 活動](https://go.microsoft.com/fwlink?LinkID=65085)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|讓您能夠在發生錯誤狀況時立即結束工作流程的作業。 [使用 TerminateActivity 活動](https://go.microsoft.com/fwlink?LinkID=65086)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|讓您能夠擷取擲回的商務例外狀況，做為工作流程其中繼資料程序的一部分。 [使用 ThrowActivity 活動](https://go.microsoft.com/fwlink?LinkID=65087)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|提供交易和例外狀況處理的架構。 如需詳細資訊，請參閱[使用 TransactionScopeActivity 活動](https://go.microsoft.com/fwlink?LinkID=65088)。|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|讓您將 Web 服務錯誤的發生頻率製成模型。 [使用 WebServiceFaultActivity 活動](https://go.microsoft.com/fwlink?LinkID=65089)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|從 Web 服務接收資料。 [使用 WebServiceInputActivity 活動](https://go.microsoft.com/fwlink?LinkID=65090)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|回應對工作流程提出的 Web 服務要求。 [使用 WebServiceOutputActivity 活動](https://go.microsoft.com/fwlink?LinkID=65092)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|讓工作流程執行迴圈，直到符合條件為止。 [使用 WhileActivity 活動](https://go.microsoft.com/fwlink?LinkID=65091)[!INCLUDE[crdefault](../includes/crdefault-md.md)]。|

 [!INCLUDE[crabout](../includes/crabout-md.md)] 如何建立自訂活動，請參閱[開發自訂活動](https://go.microsoft.com/fwlink?LinkID=65023)和[使用舊版活動設計](../workflow-designer/using-the-legacy-activity-designer.md)工具。

## <a name="in-this-section"></a>本節內容
 [即時檢視（舊版）](../workflow-designer/activity-views-legacy.md)描述活動的不同設計檢視。

 [如何：將活動新增至工具箱（舊版）](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)說明如何將活動新增至工具箱。

 [如何：建立宣告式規則條件（舊版）](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)顯示建立宣告式規則條件的步驟。

 How [to：建立 PolicyActivity 規則集（舊版）](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)顯示建立 PolicyActivity 規則集的步驟。

 [如何：執行 WCF 合約作業（舊版）](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)顯示執行 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 合約作業的步驟。

 [如何：叫用 WCF 合約作業（舊版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)顯示叫用 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 合約作業的步驟。

## <a name="see-also"></a>另請參閱
 [開發](https://go.microsoft.com/fwlink?LinkID=65010)工作流程[開發工作流程活動](https://go.microsoft.com/fwlink?LinkID=65023)的[Windows Workflow Foundation 活動](https://go.microsoft.com/fwlink?LinkID=65005)