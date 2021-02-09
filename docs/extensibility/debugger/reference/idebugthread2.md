---
title: IDebugThread2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a3eb4710e3073ee49aa9660aa322b4638c4c0d24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901612"
---
# <a name="idebugthread2"></a>IDebugThread2
這個介面代表在程式中執行的執行緒。

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表單一程式中的執行執行緒。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) 來取得此介面，以代表目前使用中的執行緒。

 此介面也用於建立中斷點要求 (請參閱 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)) 。

 解析系結或錯誤中斷點時，也會傳回這個介面 (請參閱 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 和 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)) 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugThread2` 。

|方法|描述|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|抓取這個執行緒的堆疊框架清單。|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|取得執行緒的名稱。|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|設定執行緒的名稱。|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|取得執行執行緒的程式。|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|判斷下一個語句是否可以設定為指定的堆疊框架和程式碼內容。|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|將下一個語句設定為給定的堆疊框架和程式碼內容。|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|取得系統執行緒識別碼。|
|[暫止](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|暫停執行緒。|
|[繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)|繼續執行緒。|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|取得描述執行緒的屬性。|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|取得與此實體執行緒相關聯的邏輯執行緒。|

## <a name="remarks"></a>備註
 因為單一實體執行緒可以在多個程式中執行，所以一個以上的 `IDebugThread2` 程式可以代表相同的實體執行緒。

 發生中斷點或例外狀況時，會呼叫 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)來傳送事件。 這個方法的其中一個引數是 `IDebugThread2` 代表目前線程的介面。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 是用來取得目前堆疊框架的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
