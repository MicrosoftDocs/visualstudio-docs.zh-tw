---
title: 啟動偵錯工具 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738453"
---
# <a name="launch-the-debugger"></a>啟動偵錯工具
啟動偵錯工具需要以其適當的屬性來傳送正確的方法和事件順序。

## <a name="sequences-of-methods-and-events"></a>方法和事件的順序

1. 選擇 [ **調試** 程式] 功能表，然後選擇 [ **啟動**]，即可呼叫會話 debug manager (SDM) 。 如需詳細資訊，請參閱 [啟動程式](../../extensibility/debugger/launching-a-program.md)。

2. SDM 會呼叫 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 方法。

3. 根據 debug engine (DE) 進程模型， `IDebugProgramNodeAttach2::OnAttach` 方法會傳回下列其中一種方法，以決定接下來會發生什麼事。

     如果傳回 `S_FALSE` ，則會在虛擬機器的進程中載入 debug engine (DE) 。

     -或-

     如果傳回 `S_OK` ，則會在 SDM 的進程中載入取消。 SDM 接著會執行下列工作：

    1. 呼叫 [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 以取得 DE 的引擎資訊。

    2. 共同建立 DE。

    3. 呼叫 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)。

4. DE 會將 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。

5. DE 會將 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。

6. DE 會將 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。

7. DE 會將 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。

8. DE 會將 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 傳送至具有屬性的 SDM `EVENT_SYNC` 。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
- [啟動程式](../../extensibility/debugger/launching-a-program.md)
