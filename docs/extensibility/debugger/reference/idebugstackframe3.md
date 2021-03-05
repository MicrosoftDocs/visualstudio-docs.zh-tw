---
description: 這個介面會擴充 IDebugStackFrame2 來處理攔截的例外狀況。
title: IDebugStackFrame3 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d70095db80b8bbd349509de2858b641c520b0623
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159766"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
這個介面會擴充 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 來處理攔截的例外狀況。

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 在實 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 介面的同一個物件上執行這個介面，以支援攔截的例外狀況。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)的方法外，也會 `IDebugStackFrame3` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|處理任何一般例外狀況處理之前的目前堆疊框架的例外狀況。|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|如果發生堆疊回溯，則傳回程序代碼內容。|

## <a name="remarks"></a>備註
 攔截的例外狀況表示偵錯工具可以在執行時間呼叫任何一般例外狀況處理常式之前處理例外狀況。 攔截例外狀況時，基本上表示即使沒有例外狀況處理常式，執行時間也會發出例外狀況處理常式。

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 是在所有正常的例外狀況回呼事件期間呼叫， (唯一的例外狀況是，如果您要將混合模式程式碼 (managed 和非受控碼) ，在此情況下，在最後一次可能回呼) 時無法攔截例外狀況。 如果未執行 DE `IDebugStackFrame3` ，或從 IDebugStackFrame3：： `InterceptCurrentException` (（例如 `E_NOTIMPL`) ）傳回錯誤，偵錯工具就會正常處理例外狀況。

 藉由攔截例外狀況，偵錯工具可讓使用者變更所要進行的程式狀態，然後在擲回例外狀況的位置繼續執行。

> [!NOTE]
> 攔截例外狀況只能在 managed 程式碼中使用，也就是在 Common Language Runtime (CLR) 下執行的程式。

 偵錯工具引擎表示它支援攔截例外狀況，方法是在執行時間使用函數將 "metricExceptions" 設定為1的值 `SetMetric` 。 如需詳細資訊，請參閱 [SDK helper 以進行調試](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
