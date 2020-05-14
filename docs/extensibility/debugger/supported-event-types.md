---
title: 支援的事件型態 :微軟文件
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
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712805"
---
# <a name="supported-event-types"></a>受支援的事件型態
Visual Studio 除錯目前支援以下事件型態:

- 非同步事件

   通知工作階段除錯管理員 (SDM) 和 IDE 正在除錯的應用程式的狀態正在更改。 這些事件在 SDM 和 IDE 的休閒中處理。 處理事件後,不會向調試引擎 (DE) 傳送任何回復。 [IDebug輸出StringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)和[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)介面是非同步事件的示例。

- 同步事件

   通知 SDM 和 IDE 正在除錯的應用程式的狀態正在更改。 這些事件和異步事件之間的唯一區別是,通過[「繼續從同步事件」](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)方法發送答覆。

   如果需要 DE 在 IDE 接收和處理事件後繼續處理,則發送同步事件非常有用。

- 同步停止事件或停止事件

   通知 SDM 和 IDE 正在除錯的應用程式已停止執行代碼。 當您通過方法[事件](../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件時,需要[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)參數。 通過呼叫以下方法之一繼續停止事件:

  - [執行](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [步驟](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [繼續](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    介面[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和[IDebugexceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)是停止事件的示例。

  > [!NOTE]
  > 不支援非同步停止事件。 發送非同步停止事件是錯誤的。

## <a name="discussion"></a>討論區
 事件的實際實現取決於 DE 的設計。 發送的每個事件的類型由其屬性決定,這些屬性在設計 DE 時設置。 例如,一個 DE 可以作為非同步事件傳送[IDebugProgramCreateEvent2,](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)而另一個 DE 可能會將其作為停止事件發送。

 下表指定哪些程式和線程參數需要哪些事件以及事件類型。 任何事件都可以同步。 沒有事件需要同步。

> [!NOTE]
> 所有事件都需要[IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)介面。

|事件|IDebugProgram2|IDebugThread2|停止事件|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必要|必要|是|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必要|必要|是|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必要|必要|否|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不允許|不允許|否|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不允許|不允許|否|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必要|必要|是|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|允許,但不是必需的|允許,但不是必需的|可以是|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必要|必要|是|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|允許,但不是必需的|允許,但不是必需的|可以是|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必要|必要|是|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必要|必要|是|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|允許,但不是必需的|允許,但不是必需的|可以是|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必要|允許,但不是必需的|否|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必要|允許,但不是必需的|否|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必要|允許,但不是必需的|否|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必要|允許,但不是必需的|否|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必要|允許,但不是必需的|否|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|IDebugStopCompleteEvent2|必要|必要|是|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必要|必要|是|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|允許,但不是必需的|允許,但不是必需的|否|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必要|必要|否|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必要|必要|否|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|允許,但不是必需的|允許,但不是必需的|否|

## <a name="see-also"></a>另請參閱
- [傳送事件](../../extensibility/debugger/sending-events.md)
