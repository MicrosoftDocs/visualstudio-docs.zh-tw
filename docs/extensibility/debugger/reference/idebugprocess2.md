---
title: IDebugProcess2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723806"
---
# <a name="idebugprocess2"></a>IDebugProcess2
此介面表示在埠上運行的進程。 如果埠是本地埠,則`IDebugProcess2`通常表示本地電腦上的物理進程。

## <a name="syntax"></a>語法

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由自定義埠供應商實現,以作為一個組管理程式。 此介面必須由埠供應商實現。

 如果調試引擎支援透過[Launch 暫停](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)啟動程式,則調試引擎也將實現此介面。

## <a name="notes-for-callers"></a>通話備註
 此介面主要由工作階段調試管理員 (SDM) 調用,以便與在此過程中識別的一組程式進行互動。

 調用[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)或[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)獲取此介面。 此介面也通過調用`IDebugEngineLaunch2::LaunchSuspended`返回。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcess2`。

|方法|描述|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|獲取流程的說明。|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|枚舉此過程中包含的程式。|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|獲取行程的標題、友好名稱或檔名。|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|獲取此進程運行的計算機伺服器的實例。|
|[終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|終止進程。|
|[附加](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|附加到進程。|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|確定 SDM 是否可以分離進程。|
|[中斷連結](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|從進程分離調試器。|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|獲取系統進程識別碼。|
|[取得行程 Id](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|獲取此過程的全域唯一標識符。|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> 【 已棄用】|獲取調試進程的工作階段的名稱。<br /><br /> *已棄用。 應始終返回`E_NOTIMPL`。|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|枚舉進程中運行的線程。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|請求行程中運行代碼的下一個程式停止。|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|獲取此進程正在運行的埠。|

## <a name="remarks"></a>備註
 包含`IDebugProcess2`一個或多個[IDebug Program2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。

## <a name="requirements"></a>需求
 標題: Msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [抓取程序](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [抓取程序](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
