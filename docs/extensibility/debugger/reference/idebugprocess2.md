---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bea73c1bce5367d9686e835bb58dd99a83cc818
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314133"
---
# <a name="idebugprocess2"></a>IDebugProcess2
此介面代表的連接埠上執行的程序。 如果連接埠的本機連接埠，然後`IDebugProcess2`通常代表實體的程序，在本機電腦上。

## <a name="syntax"></a>語法

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 若要以群組方式管理程式的自訂連接埠供應商提供的被實作這個介面。 透過連接埠提供者，就必須實作這個介面。

 偵錯引擎也會實作這個介面，如果它支援啟動程式通過[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。

## <a name="notes-for-callers"></a>呼叫端資訊
 此介面稱為主要是由工作階段的偵錯管理員 (SDM) 來進行互動的程式識別在這個程序中的群組。

 呼叫[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)或是[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)取得此介面。 此介面也會傳回呼叫`IDebugEngineLaunch2::LaunchSuspended`。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcess2`。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|取得處理序的描述。|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|列舉包含在此程序中的程式。|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|取得標題、 易記名稱或處理序檔案名稱。|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|取得的 server 執行此程序的機器的執行個體。|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|終止處理序。|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|將附加至處理程序。|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|決定是否 SDM 可以中斷連結程序。|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|從處理序偵錯工具會中斷連結。|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|取得系統處理序識別碼。|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|取得這個處理序的全域唯一識別碼。|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [取代]|取得正在偵錯的處理程序之工作階段的名稱。<br /><br /> [已被取代。 應該一律傳回`E_NOTIMPL`。]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|列舉在處理程序中執行的執行緒。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|要求的下一個程式在此處理程序停止執行程式碼。|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|取得的連接埠上執行此程序。|

## <a name="remarks"></a>備註
 `IDebugProcess2`包含一或多個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)