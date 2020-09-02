---
title: 評估運算式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151616"
---
# <a name="evaluating-expressions"></a>評估運算式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

運算式是從 [自動變數]、[監看式]、[快速監看式] 或 [即時運算] 視窗中傳遞 評估運算式時，它會產生可列印的字串，其中包含變數或引數的名稱和類型，以及其值。 這個字串會顯示在對應的 IDE 視窗中。  
  
## <a name="implementation"></a>實作  
 當程式在中斷點停止時，就會評估運算式。 運算式本身是以 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面表示，它代表已剖析的運算式，可在給定的運算式評估內容中進行系結和評估。 堆疊框架會決定運算式評估內容，讓 debug engine (藉由實 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面來解除) 提供。  
  
 如果指定了使用者字串和[IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面，debug ENGINE (DE) 就可以藉由將使用者字串傳遞至[IDebugExpressionCoNtext2：:P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法來取得[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。 傳回的 IDebugExpression2 介面包含已剖析的運算式可供評估。  
  
 使用 `IDebugExpression2` 介面，DE 可以使用 [IDebugExpression2：： EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [IDebugExpression2：： EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)，透過同步或非同步運算式評估來取得運算式的值。 此值以及變數或引數的名稱和類型，會傳送至 IDE 以供顯示。 值、名稱和類型會以 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面表示。  
  
 若要啟用運算式評估，DE 必須執行 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 和 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。 同步和非同步評估都需要 [IDebugProperty2：： GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法的執行。  
  
## <a name="see-also"></a>另請參閱  
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)
