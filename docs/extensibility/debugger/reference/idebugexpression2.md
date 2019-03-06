---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8027f34b48b4a160c19f14f0d9cbfb8194a506f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688469"
---
# <a name="idebugexpression2"></a>IDebugExpression2
這個介面會表示剖析的運算式可供繫結和評估。

## <a name="syntax"></a>語法

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面來代表剖析準備要評估的運算式。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)傳回此介面。 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)會傳回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 只有在已暫停，正在偵錯程式，而是可用的堆疊框架，都可以存取這些介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugExpression2`。

|方法|描述|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估此運算式。|
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式會評估此運算式。|

## <a name="remarks"></a>備註
 當程式已停止執行時，工作階段的偵錯管理員 (SDM) 會從呼叫 DE 取得堆疊框架[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然後呼叫 SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)若要取得[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 這之後藉由呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)建立`IDebugExpression2`介面，表示剖析準備要評估的運算式。

 在 SDM 撥打[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或是[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)實際評估運算式，並產生值。

 實作中`IDebugExpressionContext2::ParseText`，預設會使用 COM 的`CoCreateInstance`函式來具現化的運算式評估工具，並取得[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面 (請參閱中的範例`IDebugExpressionEvaluator`介面)。 然後呼叫 DE[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)若要取得[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)介面。 此介面用在實作`IDebugExpression2::EvaluateSync`和`IDebugExpression2::EvaluateAsync`執行評估。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)