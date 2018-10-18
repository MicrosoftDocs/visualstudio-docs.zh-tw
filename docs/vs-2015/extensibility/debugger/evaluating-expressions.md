---
title: 評估運算式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0aae7193c6840d389f7990f155fecb0149edc7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213677"
---
# <a name="evaluating-expressions"></a>評估運算式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

從 [自動變數]，監看式、 快速監看式或即時運算視窗中向下傳遞的字串，會建立運算式。 評估運算式時，它會產生可列印的字串，包含名稱和類型的變數或引數，而其值。 此字串會顯示在對應的 IDE 視窗。  
  
## <a name="implementation"></a>實作  
 程式停止於中斷點時，會評估運算式。 表示運算式本身[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，表示已剖析的運算式，可供繫結和指定的運算式評估內容中評估。 堆疊框架決定運算式評估內容，偵錯引擎 (DE) 提供藉由實作[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  
  
 指定的使用者字串和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面，偵錯引擎 (DE) 可以取得[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，藉由傳遞的使用者字串[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。 傳回的 IDebugExpression2 介面包含剖析供評估的運算式。  
  
 具有`IDebugExpression2`介面，DE 可以取得透過同步或非同步運算式評估運算式的值使用[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。 此值的名稱和類型的變數或引數，以及顯示會傳送到 IDE。 值、 名稱和型別都由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。  
  
 若要啟用運算式評估，必須實作 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)並[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 同步和非同步評估要求的實作[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)

