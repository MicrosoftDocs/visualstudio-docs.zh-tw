---
title: 工作流程設計工具的舊版工作流程活動
ms.date: 01/18/2017
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45c24c0be518e58ce87af11a38486818ca4a3ac7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="legacy-workflow-activities"></a>舊版工作流程活動

Windows Workflow Foundation (WF) 包含一組預設提供的控制流程、 條件、 事件處理、 狀態管理，以及通訊的功能，應用程式與服務活動。 在設計工作流程時，您可以使用系統提供的活動所提供的 Windows 工作流程設計工具，或您可以建立您自己的自訂活動。

下表列出 Windows Workflow Foundation 架構全新的活動組。 然而，並非所有，這些活動都由活動設計工具可以從存取**工具箱**的工作流程設計工具。 若要建立活動，其設計工具拖曳**工具箱**並將它放在設計介面上。

|活動|描述|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|搭配**HandleExternalEventActivity**活動與本機服務的輸入和輸出通訊。 如需詳細資訊，請參閱[使用 CallExternalMethodActivity 活動](http://go.microsoft.com/fwlink?LinkID=65060)。|
|**System.Workflow.Activities.CancellationHandlerActivity**|用於包含清除邏輯，適用於複合活動的所有子系完成執行前即取消複合活動時。 如需詳細資訊，請參閱[使用 CancellationHandlerActivity 活動](http://go.microsoft.com/fwlink?LinkID=65061)。|
|<xref:System.Workflow.Activities.CodeActivity>|讓您將 Visual Basic 或 C# 程式碼新增至您的工作流程。 如需詳細資訊，請參閱[使用 CodeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65062)。|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|<xref:System.Workflow.Activities.SequenceActivity> 的可補償版本。 如需詳細資訊，請參閱[使用 CompensatableSequenceActivity 活動](http://go.microsoft.com/fwlink?LinkID=65002)。|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|可補償版本**TransactionScopeActivity**。 如需詳細資訊，請參閱[使用 CompensatableTransactionScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65063)。|
|**System.Workflow.Activities.CompensateActivity**|當錯誤發生時，可讓您呼叫程式碼以復原或補償工作流程已執行的作業。 如需詳細資訊，請參閱[使用 CompensateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65064)。|
|**System.Workflow.Activities.CompensationHandlerActivity**|包裝函式之一個或多個活動的執行補償的活動已完成之 TransactionScopeActivity 活動，如需詳細資訊，請參閱[使用 CompensationHandlerActivity 活動](http://go.microsoft.com/fwlink?LinkID=65065)。|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|根據套用在 <xref:System.Workflow.Activities.ConditionedActivityGroup> 活動本身的條件，以及根據個別套用在每個子系的條件，來執行子活動。 如需詳細資訊，請參閱[使用 ConditionedActivityGroup 活動](http://go.microsoft.com/fwlink?LinkID=65066)。|
|<xref:System.Workflow.Activities.DelayActivity>|可讓您在工作流程中建置以逾時間隔為基礎的延遲。 如需詳細資訊，請參閱[使用 DelayActivity 活動](http://go.microsoft.com/fwlink?LinkID=65067)。|
|<xref:System.Workflow.Activities.EventDrivenActivity>|包裝一或多個發生指定事件時執行的活動。 如需詳細資訊，請參閱[使用 EventDrivenActivity 活動](http://go.microsoft.com/fwlink?LinkID=65068)。|
|<xref:System.Workflow.Activities.EventHandlersActivity>|提供將事件與活動產生關聯的架構。 如需詳細資訊，請參閱[使用 EventHandlersActivity 活動](http://go.microsoft.com/fwlink?LinkID=65069)。|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|執行其主要子活動，同時具有<xref:System.Workflow.Activities.EventHandlersActivity>。 如需詳細資訊，請參閱[使用 EventHandlingScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65070)。|
|**System.Workflow.Activities.FaultHandlerActivity**|用於處理您指定之類型的例外狀況。 如需詳細資訊，請參閱[使用 FaultHandlerActivity 活動](http://go.microsoft.com/fwlink?LinkID=65071)。|
|**System.Workflow.Activities.FaultHandlersActivity**|代表已排序的清單的型別其子活動的複合活動**System.Workflow.Activities.FaultHandlerActivity**。 如需詳細資訊，請參閱[使用 FaultHandlersActivity 活動](http://go.microsoft.com/fwlink?LinkID=65072)。|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|搭配<xref:System.Workflow.Activities.CallExternalMethodActivity>活動與本機服務的輸入和輸出通訊。 如需詳細資訊，請參閱[使用 HandleExternalEventActivity 活動](http://go.microsoft.com/fwlink?LinkID=65073)。|
|<xref:System.Workflow.Activities.IfElseActivity>|測試每個分支上的條件，並執行條件等於其第一個分支上的活動**true**。 如需詳細資訊，請參閱[使用 IfElseActivity 活動](http://go.microsoft.com/fwlink?LinkID=65074)。|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|表示 <xref:System.Workflow.Activities.IfElseActivity> 的分支。 如需詳細資訊，請參閱[使用 IfElseBranchActivity 活動](http://go.microsoft.com/fwlink?LinkID=65075)。|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|可讓您的工作流程叫用 Web 服務。 如需詳細資訊，請參閱[使用 InvokeWebServiceActivity 活動](http://go.microsoft.com/fwlink?LinkID=65076)。|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|可讓您的工作流程叫用另一個工作流程。 如需詳細資訊，請參閱[使用 InvokeWorkflowActivity 活動](http://go.microsoft.com/fwlink?LinkID=65077)。|
|<xref:System.Workflow.Activities.ListenActivity>|複合活動，其中只包含 <xref:System.Workflow.Activities.EventDrivenActivity> 子活動。 如需詳細資訊，請參閱[使用 ListenActivity 活動](http://go.microsoft.com/fwlink?LinkID=65078)。|
|<xref:System.Workflow.Activities.ParallelActivity>|提供方法來排程兩個以上的子**SequenceActivity**活動分支的同時處理。 如需詳細資訊，請參閱[使用 ParallelActivity 活動](http://go.microsoft.com/fwlink?LinkID=65079)。|
|<xref:System.Workflow.Activities.PolicyActivity>|用來表示規則的集合。 規則，其中包含條件和結果動作。 如需詳細資訊，請參閱[使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)。|
|<xref:System.Workflow.Activities.ReplicatorActivity>|建立單一子活動的多個執行個體。 如需詳細資訊，請參閱[使用 ReplicatorActivity 活動](http://go.microsoft.com/fwlink?LinkID=65080)。|
|<xref:System.Workflow.Activities.SequenceActivity>|提供一種簡單的方法將多個活動連結在一起，以進行循序執行。 如需詳細資訊，請參閱[使用 SequenceActivity 活動](http://go.microsoft.com/fwlink?LinkID=65081)。|
|<xref:System.Workflow.Activities.SetStateActivity>|指定轉換至新狀態。 如需詳細資訊，請參閱[使用 SetStateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65082)。|
|<xref:System.Workflow.Activities.StateActivity>|表示狀態機器工作流程中的狀態。 如需詳細資訊，請參閱[使用 StateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65083)。|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|用於<xref:System.Workflow.Activities.StateActivity>做為離開時所執行的子活動的容器活動**StateActivity**活動。 如需詳細資訊，請參閱[使用 StateFinalizationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65008)。|
|<xref:System.Workflow.Activities.StateInitializationActivity>|用於<xref:System.Workflow.Activities.StateActivity>做為輸入時所執行的子活動的容器活動**StateActivity**活動。 如需詳細資訊，請參閱[使用 StateInitializationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65006)。|
|**System.Workflow.Activities.SuspendActivity**|暫止工作流程的作業，以便在有某些需要特別注意的錯誤狀況時介入。 如需詳細資訊，請參閱[使用 SuspendActivity 活動](http://go.microsoft.com/fwlink?LinkID=65084)。|
|**System.Workflow.Activities.SynchronizationScopeActivity**|在同步化領域中循序執行所包含的活動。 如需詳細資訊，請參閱[使用 SynchronizationScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65085)。|
|**System.Workflow.Activities.TerminateActivity**|讓您能夠在發生錯誤狀況時立即結束工作流程的作業。 如需詳細資訊，請參閱[使用 TerminateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65086)。|
|**System.Workflow.Activities.ThrowActivity**|讓您能夠擷取擲回的商務例外狀況，做為工作流程其中繼資料程序的一部分。 如需詳細資訊，請參閱[使用 ThrowActivity 活動](http://go.microsoft.com/fwlink?LinkID=65087)。|
|**System.Workflow.Activities.TransactionScopeActivity**|提供異動和例外狀況處理的架構。 如需詳細資訊，請參閱[使用 TransactionScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65088)。|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|讓您將 Web 服務錯誤的發生頻率製成模型。 如需詳細資訊，請參閱[使用 WebServiceFaultActivity 活動](http://go.microsoft.com/fwlink?LinkID=65089)。|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|從 Web 服務接收資料。 如需詳細資訊，請參閱[使用 WebServiceInputActivity 活動](http://go.microsoft.com/fwlink?LinkID=65090)。|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|回應對工作流程提出的 Web 服務要求。 如需詳細資訊，請參閱[使用 WebServiceOutputActivity 活動](http://go.microsoft.com/fwlink?LinkID=65092)。|
|<xref:System.Workflow.Activities.WhileActivity>|讓工作流程執行迴圈，直到符合條件為止。 如需詳細資訊，請參閱[使用 WhileActivity 活動](http://go.microsoft.com/fwlink?LinkID=65091)。|

如需如何建立自訂活動的詳細資訊，請參閱[開發的自訂活動](http://go.microsoft.com/fwlink?LinkID=65023)和[使用舊版活動設計工具](../workflow-designer/using-the-legacy-activity-designer.md)。

## <a name="see-also"></a>另請參閱

- [Windows Workflow Foundation 活動](http://go.microsoft.com/fwlink?LinkID=65005)
- [開發工作流程](http://go.microsoft.com/fwlink?LinkID=65010)
- [開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65023)