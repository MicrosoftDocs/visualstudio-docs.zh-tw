---
description: 此介面代表在埠上執行的處理常式。
title: IDebugProcess2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d56687cb3559b5807b488fa44dfdfc4048e4c58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081603"
---
# <a name="idebugprocess2"></a>IDebugProcess2
此介面代表在埠上執行的處理常式。 如果埠是本機埠，則 `IDebugProcess2` 通常代表本機電腦上的實體處理常式。

## <a name="syntax"></a>Syntax

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由自訂埠供應商所執行，以群組的方式來管理程式。 此介面必須由埠供應商來執行。

 如果它支援透過 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)啟動程式，則 debug 引擎也會執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面主要是由會話 debug manager (SDM) 所呼叫，以便與此程式中所識別的程式群組進行互動。

 呼叫 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) 或 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) 以取得這個介面。 呼叫也會傳回這個介面 `IDebugEngineLaunch2::LaunchSuspended` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProcess2` 。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|取得進程的描述。|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|列舉此進程中包含的程式。|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|取得進程的標題、易記名稱或檔案名。|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|取得此進程正在其上執行之電腦伺服器的實例。|
|[終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|終止進程。|
|[附加](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|附加至進程。|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|判斷 SDM 是否可以卸離進程。|
|[卸離](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|卸離進程的偵錯工具。|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|取得系統處理序識別碼。|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|取得這個進程的全域唯一識別碼。|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> 否決|取得正在對進程進行偵錯工具的會話名稱。<br /><br /> 否決. 應該一律傳回 `E_NOTIMPL` 。]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|列舉在進程中執行的執行緒。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|要求在此進程中執行程式碼的下一個程式停止。|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|取得此進程正在其上執行的通訊埠。|

## <a name="remarks"></a>備註
 `IDebugProcess2`包含一或多個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
