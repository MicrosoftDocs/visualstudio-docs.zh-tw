---
title: IDebugThread2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718589"
---
# <a name="idebugthread2"></a>IDebugThread2
此介面表示在程式中運行的線程。

## <a name="syntax"></a>語法

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示單個程式中的執行線程。

## <a name="notes-for-callers"></a>通話備註
 調用[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)以獲取表示當前活動線程的此介面。

 此介面還用於創建斷點請求(請參閱[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md))。

 解析綁定或錯誤斷點時也會返回此介面(請參閱[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)和[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md))。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugThread2`。

|方法|描述|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|檢索此線程的堆疊幀的清單。|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|取得執行緒的名稱。|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|設置線程的名稱。|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|獲取運行線程的程式。|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|確定下一個語句是否可以設置為給定的堆疊框架和代碼上下文。|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|將下一個語句設置到給定的堆疊框架和代碼上下文。|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|獲取系統線程標識符。|
|[暫停](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|掛起線程。|
|[繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)|恢復線程。|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|獲取描述線程的屬性。|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|獲取與此物理線程關聯的邏輯線程。|

## <a name="remarks"></a>備註
 由於單個物理線程可以在多個程式中運行,因此多個程式中的多個`IDebugThread2`物理線程可以表示相同的物理線程。

 當發生斷點或異常時,事件通過調用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送。 此方法的參數之一`IDebugThread2`是表示當前線程的介面。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)用於獲取當前堆疊幀的[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
