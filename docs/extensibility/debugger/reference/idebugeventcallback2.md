---
title: IDebugEvent回撥2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729879"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
除錯引擎 (DE) 使用此介面向工作階段除錯管理員 (SDM) 傳送除錯事件。

## <a name="syntax"></a>語法

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]實現此介面以從調試引擎接收事件。

## <a name="notes-for-callers"></a>通話備註
 當 SDM 調用[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)或[啟動掛起](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)時,除錯引擎通常會接收此介面。 調試引擎通過調用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)向 SDM 發送事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEventCallback2`。

|方法|描述|
|------------|-----------------|
|[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|向 SDM 發送除錯事件通知。|

## <a name="remarks"></a>備註
 儘管[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)指定`IDebugEventCallback2`它們採用介面,但事實並非如此,並且介面指標將始終為空值。 相反,除錯引擎必須使用除錯中`IDebugEventCallback2`收到的介面來[連線](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)或[啟動暫停](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。

 如果套件在託管代碼中實現[IDebugEvent 回檔](../../../extensibility/debugger/reference/idebugeventcallback2.md)<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>,強烈建議 在傳遞給[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)的各種介面上調用 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
