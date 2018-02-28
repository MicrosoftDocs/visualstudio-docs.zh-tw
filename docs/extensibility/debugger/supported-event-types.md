---
title: "支援的事件類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d161b078e4001ea7f02311bbcefe4c7f1eb6b7b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="supported-event-types"></a>支援的事件類型
Visual Studio 偵錯目前支援下列事件類型：  
  
-   非同步事件  
  
     通知工作階段的偵錯管理員 (SDM) 與正在偵錯應用程式的狀態已變更的 IDE。 SDM 和 IDE 的休閒處理這些事件。 未收到回應會傳送至偵錯引擎 (DE) 中，一旦處理事件。 [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)和[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)介面是非同步事件的範例。  
  
-   同步事件  
  
     告知 SDM 和 IDE 進行偵錯應用程式的狀態會變更。 這些事件和非同步事件的唯一差異在於，藉由傳送回覆[ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)方法。  
  
     傳送同步事件是您需要繼續處理 IDE 所接收及處理事件之後您 DE 時相當實用。  
  
-   同步的停止事件，或停止事件  
  
     通知 SDM 與 IDE 已停止執行程式碼進行偵錯應用程式。 當您將停止事件傳送方法透過[事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)參數是必要項。 正在停止事件會繼續藉由呼叫下列方法的其中一個：  
  
    -   [執行](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     介面[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)會停止事件的範例。  
  
    > [!NOTE]
    >  不支援非同步停止事件。 就會傳送非同步停止事件的錯誤。  
  
## <a name="discussion"></a>討論  
 事件的實際實作，取決於您 DE 的設計。 傳送每個事件的型別取決於設計 DE 時，會設定其屬性。 例如，可能會傳送一個 DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)當做非同步事件，而另一個可能以停止事件傳送。  
  
 下表指定哪些程式和執行緒的參數所需的事件，以及事件類型。 任何事件可以是同步的。 沒有事件必須同步。  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)介面是必要的所有事件。  
  
|Event - 事件|IDebugProgram2|IDebugThread2|停止事件|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必要|必要|[是]|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必要|必要|[是]|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必要|必要|否|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允許|不允許|否|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允許|不允許|否|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必要|必要|[是]|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允許，但非必要|允許，但非必要|可以是|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必要|必要|[是]|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允許，但非必要|允許，但非必要|可以是|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必要|必要|[是]|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必要|必要|[是]|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允許，但非必要|允許，但非必要|可以是|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必要|允許，但非必要|否|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必要|允許，但非必要|否|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必要|允許，但非必要|否|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必要|允許，但非必要|否|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必要|允許，但非必要|否|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允許，但非必要|允許，但非必要|否|  
|IDebugStopCompleteEvent2|必要|必要|[是]|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必要|必要|[是]|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允許，但非必要|允許，但非必要|否|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必要|必要|否|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必要|必要|否|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允許，但非必要|允許，但非必要|否|  
  
## <a name="see-also"></a>請參閱  
 [傳送事件](../../extensibility/debugger/sending-events.md)