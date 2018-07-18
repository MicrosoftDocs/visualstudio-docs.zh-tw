---
title: 運算式評估工具架構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fdcdfef67531af40027a2dfe8c731fe9ba5128f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107159"
---
# <a name="expression-evaluator-architecture"></a>運算式評估工具架構
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示將專用語言整合到 Visual Studio 偵錯封裝，實作所需的運算式評估工具 (EE) 介面，然後呼叫的通用語言執行階段的符號提供者 (SP) 和繫結器介面。 預存程序和繫結器物件，以及目前的執行位址，會評估運算式的內容。 這些介面產生及耗用的資訊代表 EE 架構中的重要概念。  
  
## <a name="overview"></a>總覽  
  
### <a name="parsing-the-expression"></a>剖析運算式  
 當您偵錯程式時，會評估運算式的原因，但永遠在中斷點 （由使用者用來放置中斷點或其中一個例外狀況所造成） 停止偵錯的程式。 所表示的是 Visual Studio 時取得堆疊框架，目前[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面，從 偵錯引擎 (DE)。 Visual Studio 接著會呼叫[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)取得[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 此介面代表的內容，在其中的運算式可以評估;[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)是評估程序的進入點。 目前，DE 實作所有介面。  
  
 當`IDebugExpressionContext2::ParseText`是呼叫，DE 具現化與原始程式檔發生中斷點的語言關聯 EE （DE 也會具現化 SH 此時）。 由 EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面。 然後呼叫 DE[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)若要剖析的運算式 （以文字形式） 的運算式，準備好進行評估。 剖析的運算式由[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)介面。 請注意運算式時，通常剖析，並不會在此時評估。  
  
 DE 建立該物件會實作[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，將`IDebugParsedExpression`物件插入`IDebugExpression2`物件，並傳回`IDebugExpression2`物件從`IDebugExpressionContext2::ParseText`。  
  
### <a name="evaluating-the-expression"></a>評估運算式  
 Visual Studio 會呼叫  [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)評估剖析的運算式。 這兩種方法呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync`呼叫的方法，立即而`IDebugExpression2::EvaluateAsync`呼叫的方法，透過背景執行緒) 來評估剖析的運算式，並傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面代表的值和類型的已剖析的運算式。 `IDebugParsedExpression::EvaluateSync` 使用提供的 SH、 位址和繫結器將剖析的運算式轉換成實際值，由`IDebugProperty2`介面。  
  
### <a name="for-example"></a>如需範例  
 在執行中的程式遇到中斷點後，使用者選擇檢視中的變數**快速監看式** 對話方塊。 這個對話方塊會顯示變數的名稱，其值與它的型別。 使用者通常可以變更值。  
  
 當**快速監看式**對話方塊會顯示，正在檢查變數的名稱會傳送以文字的[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 這會傳回[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件，代表已剖析的運算式，在此情況下，該變數。 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)接著會呼叫產生`IDebugProperty2`物件，表示變數的值和類型，以及它的名稱。 這項資訊顯示它。  
  
 如果使用者變更變數的值[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)呼叫與新的值，變更在記憶體中變數的值，所以會使用該程式繼續時執行。  
  
 請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)如需有關這個程序的顯示變數的值。 請參閱[變更本機值](../../extensibility/debugger/changing-the-value-of-a-local.md)如需有關如何變更變數的值。  
  
## <a name="in-this-section"></a>本節內容  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供 DE 呼叫 EE 時傳遞的引數。  
  
 [主要的運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 說明撰寫 EE，以及評估內容時所需的重要介面。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [顯示 [區域變數]](../../extensibility/debugger/displaying-locals.md)   
 [變更區域變數的值](../../extensibility/debugger/changing-the-value-of-a-local.md)