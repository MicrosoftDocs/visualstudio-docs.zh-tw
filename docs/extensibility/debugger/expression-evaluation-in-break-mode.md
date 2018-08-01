---
title: 在中斷模式中的運算式評估 |Microsoft Docs
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
ms.openlocfilehash: 4afa0f98616ebcb85d421874b9c6ed5cc7270b52
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232976"
---
# <a name="expression-evaluation-in-break-mode"></a>在中斷模式中的運算式評估
下一節說明偵錯工具處於中斷模式，以及必須進行運算式評估時所發生的程序。  
  
## <a name="expression-evaluation-process"></a>運算式評估程序  
 以下是評估運算式所需的基本步驟：  
  
1.  工作階段的偵錯管理員 (SDM) 會呼叫[IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)若要取得運算式內容介面[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。  
  
2.  然後呼叫 SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)要剖析的字串。  
  
3.  如果 ParseText 沒有傳回 s_ok 時，會傳回錯誤的原因。  
  
     -否則-  
  
     如果 ParseText 確實傳回 S_OK，SDM 然後呼叫[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或是[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)從剖析的運算式取得最終的值。  
  
    -   當使用`IDebugExpression2::EvaluateSync`，指定的回呼介面進行通訊的進行中程序的評估。 最終的值都會傳入[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。  
  
    -   當使用`IDebugExpression2::EvaluateAsync`，指定的回呼介面進行通訊的進行中程序的評估。 評估完成之後，會將傳送 EvaluateAsync [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)透過回呼介面。 此事件介面後，最終的值的結果， [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)