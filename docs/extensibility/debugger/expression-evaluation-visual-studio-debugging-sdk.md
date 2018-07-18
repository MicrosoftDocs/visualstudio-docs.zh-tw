---
title: 運算式評估 (Visual Studio 偵錯 SDK) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 022a0ee21b7a58fdd69249b240490fc3c1df8361
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109801"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估 (Visual Studio 偵錯 SDK)
在中斷模式期間 IDE 必須能夠評估簡單運算式包含數個變數，您的程式。 若要達成此目的，偵錯引擎 (DE) 必須能夠剖析及評估在一個 IDE 視窗中輸入的運算式。  
  
 運算式建立使用[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法而由產生[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
 **IDebugExpression2**介面的實作方法 DE 並呼叫其**EvalAsync**方法以傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)才能顯示在 IDE 中的介面在 IDE 中的運算式評估的結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)傳回可用於將運算式的值放到監看式視窗或 [區域變數] 視窗的結構。  
  
 偵錯封裝或工作階段偵錯管理員 (SDM) 呼叫[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)取得[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示介面評估的結果。 `IDebugProperty2` 有方法可傳回名稱、 類型和運算式的值。 這項資訊會顯示各種偵錯工具視窗。  
  
## <a name="using-expression-evaluation"></a>使用運算式評估  
 若要使用運算式評估，您必須實作[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法和所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面下, 表所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估運算式。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步的運算式評估。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式評估運算式。|  
  
 評估同步和非同步要求的實作[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 非同步的運算式評估要求實作[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)