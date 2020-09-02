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
ms.openlocfilehash: fb741afd7488717ba85e68ea7fd982e3e1d5adf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849240"
---
# <a name="legacy-workflow-activities"></a>舊版工作流程活動
[!INCLUDE[wf](../includes/wf-md.md)] 包含一組預設的活動，這些活動會提供控制流程、條件、事件處理、狀態管理，以及與應用程式和服務進行通訊的功能。 設計工作流程時，您可以使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 系統提供的活動，或者建立自訂活動。

 下表列出 [!INCLUDE[wf2](../includes/wf2-md.md)] 架構全新的活動集。 您可以從的 [工具箱] 存取活動設計 **工具** 來表示這些活動的許多（但並非全部） [!INCLUDE[wfd2](../includes/wfd2-md.md)] 。 若要建立活動，請將其設計工具從 [ **工具箱** ] 拖曳至設計介面。

|活動|描述|
|--------------|-----------------|
|[CallExternalMethodActivity](https://msdn2.microsoft.com/library/system.workflow.activities.callexternalmethodactivity.aspx)|與 **HandleExternalEventActivity** 活動搭配使用，以進行與本機服務的輸入和輸出通訊。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CallExternalMethodActivity 活動](https://msdn2.microsoft.com/library/bb628493.aspx)。|
|[CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx)|用於包含清除邏輯，適用於複合活動的所有子系完成執行前即取消複合活動時。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CancellationHandlerActivity 活動](https://msdn2.microsoft.com/library/bb628604.aspx)。|
|[CodeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.codeactivity.aspx)|讓您將 Visual Basic 或 C# 程式碼新增至您的工作流程。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CodeActivity 活動](https://msdn2.microsoft.com/library/bb675249.aspx)。|
|[CompensatableSequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.compensatablesequenceactivity.aspx)|[SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx)的可補償版本。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensatableSequenceActivity 活動](https://msdn2.microsoft.com/library/bb675224.aspx)。|
|[CompensatableTransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensatabletransactionscopeactivity.aspx)|**TransactionScopeActivity**的可補償版本。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensatableTransactionScopeActivity 活動](https://msdn2.microsoft.com/library/bb628592.aspx)。|
|[CompensateActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensateactivity.aspx)|當錯誤發生時，可讓您呼叫程式碼以復原或補償工作流程已執行的作業。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensateActivity 活動](https://msdn2.microsoft.com/library/bb628608.aspx)。|
|[CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx)|一或多個活動的包裝函式，這些活動會 [!INCLUDE[crdefault](../includes/crdefault-md.md)] [使用 CompensationHandlerActivity 活動](https://msdn2.microsoft.com/library/bb675279.aspx)對已完成的 TransactionScopeActivity 活動執行補償。|
|[ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)|根據套用至 [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) 活動本身的條件，以及根據個別套用至每個子系的條件，來執行子活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ConditionedActivityGroup 活動](https://msdn2.microsoft.com/library/bb675237.aspx)。|
|[DelayActivity](https://msdn2.microsoft.com/library/system.workflow.activities.delayactivity.aspx)|可讓您在工作流程中建置以逾時間隔為基礎的延遲。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 DelayActivity 活動](https://msdn2.microsoft.com/library/bb628484.aspx)。|
|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|包裝一或多個發生指定事件時執行的活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 EventDrivenActivity 活動](https://msdn2.microsoft.com/library/bb628466.aspx)。|
|[EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx)|提供將事件與活動產生關聯的架構。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 EventHandlersActivity 活動](https://msdn2.microsoft.com/library/bb628537.aspx)。|
|[EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)|使用 [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx)同時執行其主要子活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 EventHandlingScopeActivity 活動](https://msdn2.microsoft.com/library/bb628463.aspx)。|
|[FaultHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandleractivity.aspx)|用於處理您指定之類型的例外狀況。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 FaultHandlerActivity 活動](https://msdn2.microsoft.com/library/bb628479.aspx)。|
|[FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx)|表示複合活動，此活動具有類型 [FaultHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandleractivity.aspx)之子活動的已排序清單。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 FaultHandlersActivity 活動](https://msdn2.microsoft.com/library/bb675252.aspx)。|
|[HandleExternalEventActivity](https://msdn2.microsoft.com/library/system.workflow.activities.handleexternaleventactivity.aspx)|搭配使用 [CallExternalMethodActivity](https://msdn2.microsoft.com/library/system.workflow.activities.callexternalmethodactivity.aspx) 活動與本機服務的輸入和輸出通訊。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 HandleExternalEventActivity 活動](https://msdn2.microsoft.com/library/bb628446.aspx)。|
|[IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx)|測試每個分支上的條件，並在條件等於 **true**的第一個分支上執行活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 IfElseActivity 活動](https://msdn2.microsoft.com/library/bb628472.aspx)。|
|[IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)|表示 [IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx)的分支。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 IfElseBranchActivity 活動](https://msdn2.microsoft.com/library/bb628465.aspx)。|
|[InvokeWebServiceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.invokewebserviceactivity.aspx)|可讓您的工作流程叫用 Web 服務。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 InvokeWebServiceActivity 活動](https://msdn2.microsoft.com/library/bb628576.aspx)。|
|[InvokeWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.invokeworkflowactivity.aspx)|可讓您的工作流程叫用另一個工作流程。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 InvokeWorkflowActivity 活動](https://msdn2.microsoft.com/library/bb628557.aspx)。|
|[ListenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.listenactivity.aspx)|複合活動，其中只包含 [EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx) 的子活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ListenActivity 活動](https://msdn2.microsoft.com/library/bb628468.aspx)。|
|[ParallelActivity](https://msdn2.microsoft.com/library/system.workflow.activities.parallelactivity.aspx)|提供一種方式來排程兩個或多個子 **SequenceActivity** 活動分支，以同時進行處理。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ParallelActivity 活動](https://msdn2.microsoft.com/library/bb628494.aspx)。|
|[PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)|用來表示規則的集合。 規則，其中包含條件和結果動作。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 PolicyActivity 活動](https://msdn2.microsoft.com/library/bb675229.aspx)。|
|[ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)|建立單一子活動的多個執行個體。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ReplicatorActivity 活動](https://msdn2.microsoft.com/library/bb628544.aspx)。|
|[SequenceActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequenceactivity.aspx)|提供一種簡單的方法將多個活動連結在一起，以進行循序執行。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SequenceActivity 活動](https://msdn2.microsoft.com/library/bb628551.aspx)。|
|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|指定轉換至新狀態。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SetStateActivity 活動](https://msdn2.microsoft.com/library/bb628469.aspx)。|
|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|表示狀態機器工作流程中的狀態。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 StateActivity 活動](https://msdn2.microsoft.com/library/bb628612.aspx)。|
|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|用於 [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) 活動中，做為離開 **StateActivity** 活動時所執行子活動的容器。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 StateFinalizationActivity 活動](https://msdn2.microsoft.com/library/bb675278.aspx)。|
|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|在 [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) 活動中用來作為輸入 **StateActivity** 活動時所執行子活動的容器。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 StateInitializationActivity 活動](https://msdn2.microsoft.com/library/bb675253.aspx)。|
|[SuspendActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.suspendactivity.aspx)|暫止工作流程的作業，以便在有某些需要特別注意的錯誤狀況時介入。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SuspendActivity 活動](https://msdn2.microsoft.com/library/bb628533.aspx)。|
|[SynchronizationScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.synchronizationscopeactivity.aspx)|在同步化領域中循序執行所包含的活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SynchronizationScopeActivity 活動](https://msdn2.microsoft.com/library/bb675276.aspx)。|
|[TerminateActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.terminateactivity.aspx)|讓您能夠在發生錯誤狀況時立即結束工作流程的作業。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 TerminateActivity 活動](https://msdn2.microsoft.com/library/bb675261.aspx)。|
|[ThrowActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.throwactivity.aspx)|讓您能夠擷取擲回的商務例外狀況，做為工作流程其中繼資料程序的一部分。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ThrowActivity 活動](https://msdn2.microsoft.com/library/bb628490.aspx)。|
|[TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)|提供交易和例外狀況處理的架構。 如需詳細資訊，請參閱 [使用 TransactionScopeActivity 活動](https://msdn2.microsoft.com/library/bb675241.aspx)。|
|[WebServiceFaultActivity](https://msdn2.microsoft.com/library/system.workflow.activities.webservicefaultactivity.aspx)|讓您將 Web 服務錯誤的發生頻率製成模型。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WebServiceFaultActivity 活動](https://msdn2.microsoft.com/library/bb628568.aspx)。|
|[WebServiceInputActivity](https://msdn2.microsoft.com/library/system.workflow.activities.webserviceinputactivity.aspx)|從 Web 服務接收資料。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WebServiceInputActivity 活動](https://msdn2.microsoft.com/library/bb628508.aspx)。|
|[WebServiceOutputActivity](https://msdn2.microsoft.com/library/system.workflow.activities.webserviceoutputactivity.aspx)|回應對工作流程提出的 Web 服務要求。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WebServiceOutputActivity 活動](https://msdn2.microsoft.com/library/bb628594.aspx)。|
|[WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)|讓工作流程執行迴圈，直到符合條件為止。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WhileActivity 活動](https://msdn2.microsoft.com/library/bb628552.aspx)。|

 [!INCLUDE[crabout](../includes/crabout-md.md)] 如何建立自訂活動，請參閱 [開發自訂活動](https://msdn2.microsoft.com/library/bb675248.aspx) 和 [使用舊版活動設計](../workflow-designer/using-the-legacy-activity-designer.md)工具。

## <a name="in-this-section"></a>本節內容
 [ (舊版) 的即時檢視 ](../workflow-designer/activity-views-legacy.md) 描述不同的活動設計檢視。

 [如何：將活動新增至工具箱 (舊版) ](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) 示範如何將活動加入至 [工具箱]。

 How [to：建立宣告式規則條件 (舊版) ](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)顯示建立宣告式規則條件的步驟。

 [如何：建立 PolicyActivity 規則集 (舊版) ](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) 顯示建立 PolicyActivity 規則集的步驟。

 [如何： (舊版) 執行 WCF 合約 ](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 作業顯示執行合約作業的步驟 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 。

 [如何：叫用 WCF 合約作業 (舊版) ](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) 顯示叫用合約作業的步驟 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 。

## <a name="see-also"></a>另請參閱
 [開發](https://msdn2.microsoft.com/library/bb628448.aspx)工作流程[開發工作流程活動](https://msdn2.microsoft.com/library/bb675248.aspx)的[Windows Workflow Foundation 活動](https://msdn2.microsoft.com/library/bb675247.aspx)
