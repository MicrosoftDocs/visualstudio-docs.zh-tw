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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa5a6da8d45435fc7c755905a19e95e90a98ad57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000160"
---
# <a name="legacy-workflow-activities"></a>舊版工作流程活動
[!INCLUDE[wf](../includes/wf-md.md)] 包括一組預設的活動，這組活動提供許多功能，如控制流程、條件、事件處理、狀態管理，以及與應用程式和服務相互通訊。 設計工作流程時，您可以使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 系統提供的活動，或者建立自訂活動。  
  
 下表列出 [!INCLUDE[wf2](../includes/wf2-md.md)] 架構全新的活動集。 許多，但並非全部，這些活動由活動設計工具可以從存取**工具箱**的[!INCLUDE[wfd2](../includes/wfd2-md.md)]。 若要建立活動，其設計工具拖曳**工具箱**並將它放在設計介面上。  
  
|活動|描述|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|搭配**HandleExternalEventActivity**活動與本機服務的輸入和輸出通訊。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CallExternalMethodActivity 活動](http://go.microsoft.com/fwlink?LinkID=65060)。|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|用於包含清除邏輯，適用於複合活動的所有子系完成執行前即取消複合活動時。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CancellationHandlerActivity 活動](http://go.microsoft.com/fwlink?LinkID=65061)。|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|讓您將 Visual Basic 或 C# 程式碼新增至您的工作流程。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CodeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65062)。|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|可補償版本[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensatableSequenceActivity 活動](http://go.microsoft.com/fwlink?LinkID=65002)。|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|可補償版本**TransactionScopeActivity**。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensatableTransactionScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65063)。|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|當錯誤發生時，可讓您呼叫程式碼以復原或補償工作流程已執行的作業。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65064)。|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|一或多個活動執行補償已完成之 TransactionScopeActivity 活動的包裝函式[!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 CompensationHandlerActivity 活動](http://go.microsoft.com/fwlink?LinkID=65065)。|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|執行子活動，根據條件適用於[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)活動本身以及根據個別套用在每個子系的條件。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ConditionedActivityGroup 活動](http://go.microsoft.com/fwlink?LinkID=65066)。|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|可讓您在工作流程中建置以逾時間隔為基礎的延遲。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 DelayActivity 活動](http://go.microsoft.com/fwlink?LinkID=65067)。|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|包裝一或多個發生指定事件時執行的活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 EventDrivenActivity 活動](http://go.microsoft.com/fwlink?LinkID=65068)。|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|提供將事件與活動產生關聯的架構。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 EventHandlersActivity 活動](http://go.microsoft.com/fwlink?LinkID=65069)。|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|執行其主要子活動，同時具有[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 EventHandlingScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65070)。|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|用於處理您指定之類型的例外狀況。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 FaultHandlerActivity 活動](http://go.microsoft.com/fwlink?LinkID=65071)。|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|表示一個複合活動，具有類型的子活動的已排序的清單[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 FaultHandlersActivity 活動](http://go.microsoft.com/fwlink?LinkID=65072)。|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|用於搭配[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)活動與本機服務的輸入和輸出通訊。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 HandleExternalEventActivity 活動](http://go.microsoft.com/fwlink?LinkID=65073)。|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|測試上每個分支的條件，並為其條件等於第一個分支上執行活動 **，則為 true**。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 IfElseActivity 活動](http://go.microsoft.com/fwlink?LinkID=65074)。|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|代表的分支[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 IfElseBranchActivity 活動](http://go.microsoft.com/fwlink?LinkID=65075)。|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|可讓您的工作流程叫用 Web 服務。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 InvokeWebServiceActivity 活動](http://go.microsoft.com/fwlink?LinkID=65076)。|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|可讓您的工作流程叫用另一個工作流程。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 InvokeWorkflowActivity 活動](http://go.microsoft.com/fwlink?LinkID=65077)。|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|複合活動，其中只包含[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)子活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ListenActivity 活動](http://go.microsoft.com/fwlink?LinkID=65078)。|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|可用來排定兩個或多個子**SequenceActivity**同時處理的活動分支。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ParallelActivity 活動](http://go.microsoft.com/fwlink?LinkID=65079)。|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|用來表示規則的集合。 規則，其中包含條件和結果動作。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 PolicyActivity 活動](http://go.microsoft.com/fwlink?LinkID=65004)。|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|建立單一子活動的多個執行個體。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ReplicatorActivity 活動](http://go.microsoft.com/fwlink?LinkID=65080)。|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|提供一種簡單的方法將多個活動連結在一起，以進行循序執行。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SequenceActivity 活動](http://go.microsoft.com/fwlink?LinkID=65081)。|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|指定轉換至新狀態。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SetStateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65082)。|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|表示狀態機器工作流程中的狀態。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 StateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65083)。|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|用於[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)做為離開時所執行的子活動的容器活動**StateActivity**活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 StateFinalizationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65008)。|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|用於[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)做為輸入時所執行的子活動的容器活動**StateActivity**活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 StateInitializationActivity 活動](http://go.microsoft.com/fwlink?LinkID=65006)。|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|暫止工作流程的作業，以便在有某些需要特別注意的錯誤狀況時介入。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SuspendActivity 活動](http://go.microsoft.com/fwlink?LinkID=65084)。|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|在同步化領域中循序執行所包含的活動。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 SynchronizationScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65085)。|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|讓您能夠在發生錯誤狀況時立即結束工作流程的作業。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 TerminateActivity 活動](http://go.microsoft.com/fwlink?LinkID=65086)。|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|讓您能夠擷取擲回的商務例外狀況，做為工作流程其中繼資料程序的一部分。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 ThrowActivity 活動](http://go.microsoft.com/fwlink?LinkID=65087)。|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|提供交易和例外狀況處理的架構。 如需詳細資訊，請參閱 <<c0> [ 使用 TransactionScopeActivity 活動](http://go.microsoft.com/fwlink?LinkID=65088)。|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|讓您將 Web 服務錯誤的發生頻率製成模型。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WebServiceFaultActivity 活動](http://go.microsoft.com/fwlink?LinkID=65089)。|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|從 Web 服務接收資料。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WebServiceInputActivity 活動](http://go.microsoft.com/fwlink?LinkID=65090)。|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|回應對工作流程提出的 Web 服務要求。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WebServiceOutputActivity 活動](http://go.microsoft.com/fwlink?LinkID=65092)。|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|讓工作流程執行迴圈，直到符合條件為止。 [!INCLUDE[crdefault](../includes/crdefault-md.md)][使用 WhileActivity 活動](http://go.microsoft.com/fwlink?LinkID=65091)。|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] 如何建立自訂活動，請參閱[開發的自訂活動](http://go.microsoft.com/fwlink?LinkID=65023)並[使用舊版活動設計工具](../workflow-designer/using-the-legacy-activity-designer.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [活動檢視 (舊版)](../workflow-designer/activity-views-legacy.md)  
 說明不同的活動設計檢視。  
  
 [如何：將活動新增至工具箱 (舊版)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 說明如何將活動新增至工具箱。  
  
 [如何：建立宣告式規則條件 (舊版)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 說明建立宣告式規則條件的步驟。  
  
 [如何：建立 PolicyActivity 規則集 (舊版)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 說明建立 PolicyActivity 規則集的步驟。  
  
 [如何：實作 WCF 合約作業 (舊版)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 說明實作 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 合約作業的步驟。  
  
 [如何：叫用 WCF 合約作業 (舊版)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 說明叫用 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 合約作業的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Workflow Foundation 活動](http://go.microsoft.com/fwlink?LinkID=65005)   
 [開發工作流程](http://go.microsoft.com/fwlink?LinkID=65010)   
 [開發工作流程活動](http://go.microsoft.com/fwlink?LinkID=65023)