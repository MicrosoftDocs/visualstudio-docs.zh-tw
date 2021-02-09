---
title: 中斷模式中的運算式評估 |Microsoft Docs
description: 深入瞭解偵錯工具處於中斷模式時所發生的程式，並且必須進行運算式評估。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 041e499f4c670b5b31530c7fc0ecb74358a8087f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921504"
---
# <a name="expression-evaluation-in-break-mode"></a>中斷模式中的運算式評估
下一節將描述偵錯工具處於中斷模式且必須進行運算式評估時所發生的程式。

## <a name="expression-evaluation-process"></a>運算式評估程式
 以下是評估運算式所牽涉到的基本步驟：

1. 會話 debug manager (SDM) 呼叫 [IDebugStackFrame2：： GetExpressionCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 來取得運算式內容介面 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。

2. SDM 接著會使用要剖析的字串來呼叫 [IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 。

3. 如果 ParseText 未傳回 S_OK，則會傳回錯誤的原因。

     相反

     如果 ParseText 傳回 S_OK，則 SDM 可呼叫 [IDebugExpression2：： EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2：： EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ，以從剖析的運算式取得最終值。

    - 使用時 `IDebugExpression2::EvaluateSync` ，指定的回呼介面會傳達進行中的評估程式。 最後一個值會在 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面中傳回。

    - 使用時 `IDebugExpression2::EvaluateAsync` ，指定的回呼介面會傳達進行中的評估程式。 評估完成後，EvaluateAsync 會透過回呼傳送 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 介面。 使用這個事件介面時，最終的值會以 [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)結果。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
