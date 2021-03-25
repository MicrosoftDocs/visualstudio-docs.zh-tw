---
description: 這個介面表示 (DE) 的 debug engine。
title: IDebugEngine2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e32c4798ad1bea65a9aadcf8a0d73052acc238
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066148"
---
# <a name="idebugengine2"></a>IDebugEngine2
這個介面表示 (DE) 的 debug engine。 它是用來管理偵錯工具會話的各個層面，從建立中斷點到設定和清除例外狀況。

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面是由自訂的 DE 來執行，以管理程式的偵錯工具。 這個介面必須由 DE 來執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 會話 debug manager (SDM) 呼叫此介面來管理偵錯工具，包括管理例外狀況、建立中斷點，以及回應 DE 傳送的同步事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugEngine2` 。

|方法|描述|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|針對正在由 DE 進行調試的所有程式建立列舉值。|
|[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)|將 DE 附加至程式。|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|在 DE 中建立暫止中斷點。|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|指定 DE 應該如何處理指定的例外狀況。|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|移除指定的例外狀況，使它不再由 debug 引擎處理。|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|移除 IDE 已針對特定執行時間架構或語言設定的例外狀況清單。|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|取得 DE 的 GUID。|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|告知刪除指定的程式已被異常終止，而 DE 應該清除程式的所有參考，並傳送程式損毀事件。|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|由 SDM 呼叫，以表示已接收並處理之前由 DE 傳送給 SDM 的同步偵錯工具事件。|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|設定 DE 的地區設定。|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|設定 DE 目前正在使用的登錄根目錄。|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|設定度量。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|要求所有由這個取消執行的程式會在下一個執行緒嘗試執行時停止執行。|

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
