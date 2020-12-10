---
title: 支援的事件種類 |Microsoft Docs
description: 瞭解 Visual Studio 偵錯工具支援的事件種類，包括非同步事件、同步事件和停止事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 215256cbbcff45dfa0b85a480f0900e6f8ddfa71
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996028"
---
# <a name="supported-event-types"></a>支援的事件種類
Visual Studio 的偵測目前支援下列事件種類：

- 非同步事件

   通知會話 debug manager (SDM) 和 IDE，表示正在進行調試的應用程式狀態正在變更。 這些事件會在 SDM 和 IDE 的休閒中處理。 一旦處理事件，就不會將回復傳送至 debug engine (DE) 。 [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)和[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)介面是非同步事件的範例。

- 同步事件

   通知 SDM 和 IDE，正在進行正在進行調試的應用程式狀態變更。 這些事件和非同步事件之間的唯一差異在於，回復是透過 [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 方法來傳送。

   如果您需要在 IDE 接收和處理事件之後，讓您的 DE 繼續處理，則傳送同步事件會很有用。

- 同步停止事件或停止事件

   通知 SDM 和 IDE，表示正在調試的應用程式已停止執行程式碼。 當您透過方法 [事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)傳送停止事件時，需要 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 參數。 藉由呼叫下列其中一種方法，可繼續停止事件：

  - [執行](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [繼續](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)介面是停止事件的範例。

  > [!NOTE]
  > 不支援非同步停止事件。 傳送非同步停止事件是錯誤的。

## <a name="discussion"></a>討論
 實際的事件執行取決於您的 DE 的設計。 每個傳送事件的類型取決於您設計 DE 時所設定的屬性。 例如，一個 DE 可能會以非同步事件傳送 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ，而另一個則會將它傳送為停止事件。

 下表指定哪些程式和執行緒參數需要哪些事件，以及事件種類。 任何事件都可以同步。 無事件需要同步。

> [!NOTE]
> 所有事件都需要 [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) 介面。

|事件|IDebugProgram2|IDebugThread2|停止事件|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允許但非必要|允許但非必要|否|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必要|必要|是|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允許但非必要|允許但非必要|否|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允許但非必要|允許但非必要|否|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允許但非必要|允許但非必要|否|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必要|必要|是|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必要|必要|否|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允許|不允許|否|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允許|不允許|否|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必要|必要|是|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允許但非必要|允許但非必要|可以是|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必要|必要|是|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允許但非必要|允許但非必要|可以是|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必要|必要|是|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必要|必要|是|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允許但非必要|允許但非必要|可以是|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必要|允許但非必要|否|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允許但非必要|允許但非必要|否|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必要|允許但非必要|否|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必要|允許但非必要|否|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必要|允許但非必要|否|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必要|允許但非必要|否|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允許但非必要|允許但非必要|否|
|IDebugStopCompleteEvent2|必要|必要|是|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必要|必要|是|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允許但非必要|允許但非必要|否|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必要|必要|否|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必要|必要|否|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允許但非必要|允許但非必要|否|

## <a name="see-also"></a>另請參閱
- [傳送事件](../../extensibility/debugger/sending-events.md)
