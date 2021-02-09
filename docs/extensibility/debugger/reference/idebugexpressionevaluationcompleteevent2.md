---
title: IDebugExpressionEvaluationCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74e31339b48e49869ce76ce9a3b20a14dcb0acf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930456"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
當非同步運算式評估完成時，debug engine 會將這個介面傳送 (DE) 至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以報告完成呼叫 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)所開始的運算式評估。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以報告運算式評估的完成。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugExpressionEvaluationCompleteEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|取得原始的運算式。|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|取得運算式評估的結果。|

## <a name="remarks"></a>備註
 無論評估成功與否，DE 都必須傳送此事件。

 如果評估不成功， `DEBUG_PROPINFO_VALUE` `DEBUG_PROPINFO_ATTRIB` 就不會在[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)所傳回的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構中設定和旗標 ([IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件是由 DE 所建立， `IDebugExpressionEvaluationCompleteEvent2` 如果評估失敗) ，則會在事件中傳回。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
