---
title: 運算式評估 (Visual Studio 調試 SDK) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562155"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估 (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在中斷模式期間，IDE 必須能夠評估涉及程式之數個變數的簡單運算式。 為了達成此目的，debug engine (DE) 必須能夠剖析和評估輸入至 IDE 其中一個視窗的運算式。  
  
 運算式是使用 [IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法來建立，並由產生的 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面表示。  
  
 **IDebugExpression2**介面是由 DE 所執行，並呼叫其**EvalAsync**方法以將[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面傳回 ide，以便在 ide 中顯示運算式評估的結果。 [IDebugProperty2：： GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 會傳回結構，可用來將運算式的值放入監看式視窗或 [區域變數] 視窗中。  
  
 Debug 封裝或會話 debug manager (SDM) 呼叫 [IDebugExpression2：： EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 或 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 來取得代表評估結果的 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面。 `IDebugProperty2` 有方法可傳回運算式的名稱、類型和值。 這項資訊會顯示在各種偵錯工具視窗中。  
  
## <a name="using-expression-evaluation"></a>使用運算式評估  
 若要使用運算式評估，您必須執行 [IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法和 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面的所有方法，如下表所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估運算式。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式評估運算式。|  
  
 同步和非同步評估需要 [IDebugProperty2：： GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法的執行。 非同步運算式評估需要執行 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
