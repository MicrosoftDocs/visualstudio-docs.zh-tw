---
title: 中斷模式中的運算式評估 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152751"
---
# <a name="expression-evaluation-in-break-mode"></a>中斷模式中的運算式評估
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明偵錯工具處於中斷模式，且必須進行運算式評估時所發生的程式。  
  
## <a name="expression-evaluation-process"></a>運算式評估程式  
 以下是評估運算式所牽涉到的基本步驟：  
  
1. 會話 debug manager (SDM) 呼叫 [IDebugStackFrame2：： GetExpressionCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 來取得運算式內容介面 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。  
  
2. SDM 接著會使用要剖析的字串來呼叫 [IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 。  
  
3. 如果 ParseText 未傳回 S_OK，則會傳回錯誤的原因。  
  
     相反  
  
     如果 ParseText 傳回 S_OK，則 SDM 接著可以呼叫 [IDebugExpression2：： EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2：： EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ，以從剖析的運算式取得最終值。  
  
    - 在使用的情況下 `IDebugExpression2::EvaluateSync` ，會使用指定的回呼介面來傳達正在進行的評估程式。 最後一個值會在 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面中傳回。  
  
    - 在使用的情況下 `IDebugExpression2::EvaluateAsync` ，會使用指定的回呼介面來傳達正在進行的評估程式。 評估完成後，EvaluateAsync 會透過回呼傳送 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 介面。 使用這個事件介面時，可以使用 [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)取得最終的值。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
