---
title: 評估運算式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-expressions"></a>評估運算式
運算式會建立從 [自動變數]、 監看式、 快速監看式或立即的 windows 中傳遞的字串。 評估運算式時，它會產生可列印的字串，包含名稱和類型變數或引數和其值。 這個字串會顯示在對應的 IDE 視窗中。  
  
## <a name="implementation"></a>實作  
 當程式在中斷點停止時，會評估運算式。 運算式本身由[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，表示已繫結和指定的運算式評估內容內評估的已剖析的運算式。 堆疊框架判斷運算式的評估內容，偵錯引擎 (DE) 提供藉由實作[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  
  
 指定使用者字串和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面，可以取得偵錯引擎 (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面傳遞至的使用者字串[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。 傳回 IDebugExpression2 介面包含剖析準備好進行評估的運算式。  
  
 與`IDebugExpression2`介面，DE 可以取得透過同步或非同步的運算式評估運算式的值使用[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。 顯示此值的名稱和類型的變數或引數，以及傳送給 IDE。 值、 名稱和類型都由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。  
  
 若要啟用運算式的評估，必須實作 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 評估同步和非同步要求的實作[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)