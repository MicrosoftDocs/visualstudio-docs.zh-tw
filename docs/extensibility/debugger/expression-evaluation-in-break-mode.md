---
title: 中斷模式下的運算 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738730"
---
# <a name="expression-evaluation-in-break-mode"></a>中斷模式下的運算
以下部分介紹調試器處於中斷模式且必須執行表達式計算時發生的過程。

## <a name="expression-evaluation-process"></a>運算式評估程序
 以下是計算運算式所涉及的基本步驟:

1. 工作階段除錯管理員 (SDM) 呼叫[IDebugStackFrame2:::取得運算式上下文](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)以取得運算式上下文介面[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)。

2. 然後,SDM 調用[IDebugExpressionContext2::ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)該字串將被解析。

3. 如果 ParseText 未返回S_OK,則返回錯誤的原因。

     -否則

     如果 ParseText 確實返回S_OK,則 SDM 可以調用[IDebugExpression2:::計算同步](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::評估Async](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)從解析的運算式中獲取最終值。

    - 使用`IDebugExpression2::EvaluateSync`時,給定的回調介面將傳達評估的持續過程。 最終值在[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面中返回。

    - 使用`IDebugExpression2::EvaluateAsync`時,給定的回調介面將傳達評估的持續過程。 評估完成後,評估 Async 將透過回覆送出[IDebugExpression 評估完成事件 2 介面](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。 使用此事件介面,最終值將產生[GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
