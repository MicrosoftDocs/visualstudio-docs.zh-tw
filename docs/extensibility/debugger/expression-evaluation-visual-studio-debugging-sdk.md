---
title: 運算式評估 (Visual Studio 調試 SDK) |Microsoft Docs
description: 在中斷模式期間，IDE 會評估涉及程式變數的運算式。 瞭解 debug engine 如何剖析和評估運算式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e6a79a3268f0bd4acebde795109d39466032a2f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096794"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估 (Visual Studio 調試 SDK) 
在中斷模式期間，IDE 必須評估涉及數個程式變數的簡單運算式。 若要完成其評估，debug engine (DE) 必須剖析和評估輸入至 IDE 其中一個視窗的運算式。

 運算式會以 [IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法建立，並以產生的 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面表示。

 **IDebugExpression2** 介面是由 DE 所執行，並呼叫其 **EvalAsync** 方法以將 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面傳回 ide，以便在 ide 中顯示運算式評估的結果。 [IDebugProperty2：： GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 會傳回用來將運算式的值放入 **[監看** 式] 視窗或 [ **區域變數** ] 視窗中的結構。

 Debug 封裝或會話 debug manager (SDM) 呼叫 [IDebugExpression2：： EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 或 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 來取得代表評估結果的 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面。 `IDebugProperty2` 有方法可傳回運算式的名稱、類型和值。 這項資訊會出現在各種偵錯工具視窗中。

## <a name="using-expression-evaluation"></a>使用運算式評估
 若要使用運算式評估，您必須執行 [IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法和 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面的所有方法，如下表所示。

|方法|描述|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估運算式。|
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式評估運算式。|

 同步和非同步評估需要執行 [IDebugProperty2：： GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法。 非同步運算式評估需要執行 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
