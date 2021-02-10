---
title: IDebugExpression2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d7b6508a635edf3dc328f79a06a386efce07aae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949580"
---
# <a name="idebugexpression2"></a>IDebugExpression2
這個介面代表已剖析的運算式，可供進行系結和評估。

## <a name="syntax"></a>Syntax

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表可供評估的已剖析運算式。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 的呼叫會傳回這個介面。 [GetExpressionCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 會傳回 [IDebugExpressionCoNtext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。 只有在正在進行程式設計的程式已暫停，而且有堆疊框架可用時，才可以存取這些介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugExpression2` 。

|方法|描述|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估此運算式。|
|[中止](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式評估此運算式。|

## <a name="remarks"></a>備註
 當程式停止時，會話 debug manager (SDM) 從 EnumFrameInfo 取得堆疊框架，並呼叫[](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 SDM 接著會呼叫 [GetExpressionCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 來取得 [IDebugExpressionCoNtext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。 接下來是呼叫 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 來建立 `IDebugExpression2` 介面，此介面表示準備要評估的已剖析運算式。

 SDM 會呼叫 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ，以實際評估運算式並產生值。

 在的實中 `IDebugExpressionContext2::ParseText` ，DE 會使用 COM 的函 `CoCreateInstance` 式來具現化運算式評估工具並取得 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 介面 (請參閱介面) 中的範例 `IDebugExpressionEvaluator` 。 然後，會呼叫 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 來取得 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 介面。 此介面會在的 `IDebugExpression2::EvaluateSync` 執行和中用 `IDebugExpression2::EvaluateAsync` 來執行評估。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
