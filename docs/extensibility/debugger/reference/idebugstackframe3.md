---
title: IDebugStackFrame3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719477"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
此介面擴展[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)以處理截獲的異常。

## <a name="syntax"></a>語法

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 在實現[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面以支援截獲的異常的同一對象上實現此介面。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugStackFrame2`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)繼承的方法`IDebugStackFrame3`外, 還公開了以下方法。

|方法|描述|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|在任何常規異常處理之前處理當前堆疊幀的異常。|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|如果要進行堆疊展開,則返回代碼上下文。|

## <a name="remarks"></a>備註
 截獲的異常意味著調試器可以在運行時調用任何正常異常處理例程之前處理異常。 攔截異常實質上意味著使運行時假裝存在異常處理程式,即使沒有異常處理程式。

- 在所有正常異常回調事件(唯一的例外是調試混合模式代碼(託管和非託管代碼)期間調用[InterceptCurrentException,](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)在這種情況下,在最後一次回叫期間無法截獲異常)。 如果 DE`IDebugStackFrame3`未實現 ,或者 DE 傳回 IDebugStackFrame3::(`InterceptCurrentException`如`E_NOTIMPL`)的錯誤,則調試器將正常處理異常。

 通過攔截異常,調試器可以允許使用者對正在調試的程式的狀態進行更改,然後在引發異常時恢復執行。

> [!NOTE]
> 僅在託管代碼中允許截獲的異常,即在「通用語言運行時 (CLR)」下運行的程式中允許截獲的異常。

 除錯引擎表示它支援透過使用`SetMetric`函數在執行時將「metricExceptions」設置為 1 的值來攔截異常。 有關詳細資訊,請參閱[用於除錯 的 SDK 協助器](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
