---
title: 在中斷模式中的運算式評估 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66c69d6dc3dbce328e519f6d078e0aa4a5208ca0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100282"
---
# <a name="expression-evaluation-in-break-mode"></a>在中斷模式中的運算式評估
以下說明當偵錯工具處於中斷模式，但必須進行運算式評估所發生的程序。  
  
## <a name="expression-evaluation-process"></a>運算式評估程序  
 這些是在評估運算式時所需的基本步驟：  
  
1.  工作階段的偵錯管理員 (SDM) 呼叫[IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)獲得的運算式內容介面， [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。  
  
2.  然後呼叫 SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)與要剖析的字串。  
  
3.  如果 ParseText 不會傳回 S_OK 時，會傳回錯誤的原因。  
  
     -否則-  
  
     如果 ParseText 確實傳回 S_OK，SDM 可以呼叫[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)取得最後一個值從已剖析的運算式。  
  
    -   如果使用`IDebugExpression2::EvaluateSync`，用來通訊的進行中程序的評估指定的回呼介面。 則會傳回最後值[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。  
  
    -   如果使用`IDebugExpression2::EvaluateAsync`，用來通訊的進行中程序的評估指定的回呼介面。 當評估完成之後，會將傳送 EvaluateAsync [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)透過回呼介面。 可以透過取得與此事件介面的最終值[GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)