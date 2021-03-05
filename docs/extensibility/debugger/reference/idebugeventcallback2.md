---
description: 此介面是由 debug engine (DE) 將 debug 事件傳送到會話 debug manager (SDM) 。
title: IDebugEventCallback2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb33bcbdff14b0f95aab5d8f300473c13d4c342f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152906"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
此介面是由 debug engine (DE) 將 debug 事件傳送到會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 會執行這個介面，以從 debug engine 接收事件。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當 SDM 呼叫 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)或 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)時，debug engine 通常會收到這個介面。 偵錯工具引擎會呼叫 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)，將事件傳送至 SDM。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugEventCallback2` 。

|方法|描述|
|------------|-----------------|
|[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|將偵測事件的通知傳送至 SDM。|

## <a name="remarks"></a>備註
 雖然 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 和 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 會指定它們採用 `IDebugEventCallback2` 介面，但這並不是這種情況，而且介面指標一律為 null 值。 相反地，debug engine 必須使用 `IDebugEventCallback2` 呼叫中所接收的介面來 [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)或 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。

 如果封裝在 managed 程式碼中執行 [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) ，強烈建議您在 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 傳遞至 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)的各種介面上叫用。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
