---
title: 支援的事件類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d74448479fc71af493ef720586541d92d614b24f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696294"
---
# <a name="supported-event-types"></a>支援的事件類型
Visual Studio 偵錯目前支援下列事件類型：

- 非同步事件

   通知工作階段的偵錯管理員 (SDM) 和正在偵錯的應用程式狀態正在變更的 IDE。 在 SDM 和 IDE 的休閒以處理這些事件。 處理事件之後，偵錯引擎 (DE) 會不傳送任何回應。 [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)並[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)介面是非同步事件的範例。

- 同步事件

   通知的 SDM 和正在偵錯的應用程式狀態正在變更的 IDE。 這些事件與非同步事件之間唯一的差別是，藉由傳送回覆[ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)方法。

   傳送同步的事件是需要您 DE 以繼續處理之後 IDE 會接收及處理事件時相當實用。

- 同步的停止事件，或停止事件

   通知應用程式進行偵錯已停止執行程式碼在 SDM 和 IDE。 當您透過此方法，會在傳送停止事件時[事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)，則[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)是必要參數。 正在停止事件會繼續藉由呼叫下列方法其中一個：

  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    介面[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)並[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)會停止事件的範例。

  > [!NOTE]
  >  不支援非同步停止事件。 它是傳送非同步停止事件中的錯誤。

## <a name="discussion"></a>討論
 事件的實際實作取決於您的德國的設計。 傳送每個事件的型別取決於其屬性，當您設計 DE 時設定。 比方說，可能會傳送一個 DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)當做非同步事件，而另一個可能會將它傳送為停止事件。

 下表指定哪些程式和執行緒的參數所需的事件，以及事件類型。 任何事件可以是同步的。 不必須要同步的任何事件。

> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)介面是必要的所有事件。

|Event - 事件|IDebugProgram2|IDebugThread2|停止事件|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允許，但非必要|允許，但非必要|否|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必要|必要|是|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允許，但非必要|允許，但非必要|否|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允許，但非必要|允許，但非必要|否|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允許，但非必要|允許，但非必要|否|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必要|必要|是|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必要|必要|否|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允許|不允許|否|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允許|不允許|否|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必要|必要|是|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允許，但非必要|允許，但非必要|可以是|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必要|必要|是|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允許，但非必要|允許，但非必要|可以是|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必要|必要|是|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必要|必要|是|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允許，但非必要|允許，但非必要|可以是|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必要|允許，但非必要|否|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允許，但非必要|允許，但非必要|否|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必要|允許，但非必要|否|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必要|允許，但非必要|否|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必要|允許，但非必要|否|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必要|允許，但非必要|否|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允許，但非必要|允許，但非必要|否|
|IDebugStopCompleteEvent2|必要|必要|是|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必要|必要|是|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允許，但非必要|允許，但非必要|否|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必要|必要|否|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必要|必要|否|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允許，但非必要|允許，但非必要|否|

## <a name="see-also"></a>另請參閱
- [傳送事件](../../extensibility/debugger/sending-events.md)