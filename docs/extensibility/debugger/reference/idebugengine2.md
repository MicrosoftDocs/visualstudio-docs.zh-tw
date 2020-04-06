---
title: IDebugEngine2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730858"
---
# <a name="idebugengine2"></a>IDebugEngine2
此介面表示調試引擎 (DE)。 它用於管理調試會話的各個方面,從創建斷點到設置和清除異常。

## <a name="syntax"></a>語法

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由自定義 DE 實現,用於管理程式的調試。 此介面必須由 DE 實現。

## <a name="notes-for-callers"></a>通話備註
 工作階段除錯管理員 (SDM) 呼叫此介面來管理除錯工作階段,包括管理異常、創建斷點和回應 DE 發送的同步事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEngine2`。

|方法|描述|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|為 DE 正在除錯的所有程式建立枚舉器。|
|[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)|將 DE 附加到程式。|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|在 DE 中創建掛起的斷點。|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|指定 DE 應如何處理給定的異常。|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|刪除指定的異常,以便調試引擎不再處理它。|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|刪除 IDE 為特定執行時體系結構或語言設置的異常清單。|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|獲取 DE 的 GUID。|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|通知 DE 指定的程式已終止,並且 DE 應清除對程式的所有引用並發送程式銷毀事件。|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|SDM 呼叫以指示接收和處理以前 DE 發送到 SDM 的同步調試事件。|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|設置 DE 區域設置。|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|設置 DE 目前正在使用的註冊表根。|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|設置指標。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|請求此 DE 正在除錯的所有程式在下次線程嘗試執行時停止執行。|

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
