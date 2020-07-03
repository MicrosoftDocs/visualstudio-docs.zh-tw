---
title: 附加和卸離程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a751e6aa70c1aacd5df598e0c0e62da3b9d14b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903158"
---
# <a name="attaching-and-detaching-to-a-program"></a>附加和卸離程式
附加偵錯工具時，必須使用適當的屬性來傳送正確的方法和事件順序。

## <a name="sequence-of-methods-and-events"></a>方法和事件的順序

1. 會話 debug manager （SDM）會呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。

    根據 debug engine （DE）進程模型， `IDebugProgramNodeAttach2::OnAttach` 方法會傳回下列其中一種方法，以判斷接下來會發生什麼事。

    如果 `S_FALSE` 傳回，則表示已成功將 debug engine 附加至程式。 否則，會呼叫[attach](../../extensibility/debugger/reference/idebugengine2-attach.md)方法來完成附加程式。

    如果 `S_OK` 傳回，則會在與 SDM 相同的進程中載入 DE。 SDM 會執行下列工作：

   1. 呼叫[GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)以取得 DE 的引擎資訊。

   2. 共同建立 DE。

   3. 呼叫[Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)。

2. DE 會將[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)傳送至具有屬性的 SDM `EVENT_SYNC` 。

3. DE 會將[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)傳送至具有屬性的 SDM `EVENT_SYNC` 。

4. DE 會將[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)傳送至具有屬性的 SDM `EVENT_SYNC_STOP` 。

   卸離程式是一種簡單、兩個步驟的流程，如下所示：

5. SDM 呼叫卸[離](../../extensibility/debugger/reference/idebugprogram2-detach.md)。

6. DE 會傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
