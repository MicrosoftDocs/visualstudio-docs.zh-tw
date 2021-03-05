---
description: 當目前正在執行的程式中擲回例外狀況時，debug engine (DE) 會將此介面傳送至會話 debug manager (SDM) 。
title: IDebugExceptionEvent2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e171154d933ac533f6a63469321b5a0d22e8651b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152763"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
當目前正在執行的程式中擲回例外狀況時，debug engine (DE) 會將此介面傳送至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以報告正在進行調試的程式中發生例外狀況。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件來報告例外狀況。 事件是使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送，該函式是由 SDM 附加至正在進行調試的程式時所提供的函式。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugExceptionEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|取得引發這個事件之例外狀況的詳細資訊。|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|取得引發這個事件之擲回例外狀況的人們可讀取描述。|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|決定 debug engine (DE) 是否支援將這個例外狀況傳遞至執行繼續時所要進行偵錯工具的選項。|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|指定是否應將例外狀況傳遞至執行繼續時所要進行的程式，或者是否應捨棄例外狀況。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>備註
 傳送事件之前，會先檢查此例外狀況事件是否已指定為先前呼叫 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)的第一個機會或第二個例外狀況。 如果已指定為第一個可能發生的例外狀況，則 `IDebugExceptionEvent2` 會將事件傳送至 SDM。 如果沒有，則會讓應用程式有機會處理例外狀況。 如果未提供任何例外狀況處理常式，而且已將例外狀況指定為第二個例外狀況，則 `IDebugExceptionEvent2` 會將事件傳送至 SDM。 否則，就會繼續執行程式，而作業系統或執行時間會處理例外狀況。

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
