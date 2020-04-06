---
title: IDebugExpression2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729686"
---
# <a name="idebugexpression2"></a>IDebugExpression2
此介面表示可供綁定和評估的解析表達式。

## <a name="syntax"></a>語法

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示準備計算的解析表達式。

## <a name="notes-for-callers"></a>通話備註
 對[ParseText 的](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)呼叫將返回此介面。 [getExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)傳回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 僅當正在調試的程式已暫停且堆疊幀可用時,才能訪問這些介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugExpression2`。

|方法|描述|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|非同步計算此運算式。|
|[中止](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步表達式計算。|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|同步計算此運算式。|

## <a name="remarks"></a>備註
 當程式停止時,工作階段除錯管理員 (SDM) 從 DE 取得一個堆疊幀,並呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然後,SDM 調用[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)來獲取[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 然後調用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)`IDebugExpression2`以建立 介面,該介面表示可計算的解析運算式。

 SDM 調用[評估同步](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[評估 Async](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)來實際評估運算式並生成值。

 在實現中`IDebugExpressionContext2::ParseText`,DE 使用`CoCreateInstance`COM 的函數實例化運算式賦值器並獲得[IDebugExpression 評估器](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)`IDebugExpressionEvaluator`介面(請參閱介面中 的範例)。 然後,DE 調用[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)以獲取[IDebugparsed 運算式](../../../extensibility/debugger/reference/idebugparsedexpression.md)介面。 此介面用於實現`IDebugExpression2::EvaluateSync`和執行`IDebugExpression2::EvaluateAsync`評估。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
