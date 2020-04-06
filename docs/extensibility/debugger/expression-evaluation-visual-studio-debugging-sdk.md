---
title: 表達式評估(可視化工作室調試 SDK) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738708"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估(視覺化工作室除錯 SDK)
在中斷模式下,IDE 必須計算涉及多個程式變數的簡單表達式。 為了完成其計算,調試引擎 (DE) 必須解析和評估輸入到 IDE 視窗之一的運算式。

 運算式使用[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法建立,並由生成的[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面表示。

 **IDebugExpression2**介面由 DE 實現,並調用其**EvalAsync**方法將[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面返回到 IDE,以便在 IDE 中顯示表達式計算的結果。 [IDebugProperty2:getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)傳回結構,用於將表示式的值放入 **「監視」** 視窗或 **「局部變數」** 視窗中。

 除錯套件或工作階段除錯管理員 (SDM) 呼叫[IDebugExpression2::評估Async](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或[評估同步](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md),以獲得表示評估結果的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。 `IDebugProperty2`具有返回表達式的名稱、類型和值的方法。 此資訊將顯示在各種除錯器視窗中。

## <a name="using-expression-evaluation"></a>使用表示式運算
 要使用運算式計算,必須實現[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法以及[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面的所有方法,如下表所示。

|方法|描述|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|非同步計算運算式。|
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步表達式計算。|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|同步計算運算式。|

 同步和非同步評估需要實現[IDebugProperty2::getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 同步表示式計算要求實現[IDebug 表示式計算完成事件2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。

## <a name="see-also"></a>另請參閱
- [執行控制及狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
