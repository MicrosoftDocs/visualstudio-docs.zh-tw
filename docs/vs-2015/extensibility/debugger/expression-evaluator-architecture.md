---
title: 運算式評估工具架構 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0aa8f5cc45e0f6e012ecb3f0a27a22725a259
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421219"
---
# <a name="expression-evaluator-architecture"></a>運算式評估工具架構
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 表示將專屬的語言整合到 Visual Studio 偵錯封裝，實作所需的運算式評估工具 (EE) 介面和呼叫的通用語言執行階段的符號提供者 (SP) 和繫結器介面。 預存程序和繫結器的物件，以及目前執行的位址，會在其中評估運算式的內容。 這些介面產生及耗用的資訊代表 EE 的架構的重要概念。  
  
## <a name="overview"></a>總覽  
  
### <a name="parsing-the-expression"></a>剖析運算式  
 當您偵錯程式時，運算式會評估將多個原因，但一律在中斷點 （放在使用者的中斷點或其中一個例外狀況所造成） 停止正在進行偵錯的程式。 表示的是 Visual Studio 時取得堆疊框架，此時[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面，從 偵錯引擎 (DE)。 Visual Studio 接著會呼叫[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)若要取得[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 這個介面表示在其中您可以評估運算式; 的內容[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)是評估程序的進入點。 目前，德國實作所有介面。  
  
 當`IDebugExpressionContext2::ParseText`是呼叫，DE 具現化發生中斷點的原始程式檔的語言與相關聯 EE （DE 也會具現化 SH 此時）。 表示 EE [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面。 然後呼叫 DE[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)若要剖析的運算式中轉換的運算式 （以文字形式），您可以準備進行評估。 這個已剖析的運算式由[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)介面。 請注意，通常會剖析並不會在此時評估運算式。  
  
 DE 會建立該物件會實作[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面，讓`IDebugParsedExpression`物件插入`IDebugExpression2`物件，並傳回`IDebugExpression2`物件`IDebugExpressionContext2::ParseText`。  
  
### <a name="evaluating-the-expression"></a>評估運算式  
 Visual Studio 會呼叫其中一個[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或是[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)評估已剖析的運算式。 這兩種方法呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync`呼叫的方法立即執行，而`IDebugExpression2::EvaluateAsync`呼叫的方法，透過在背景執行緒) 來評估已剖析的運算式，並傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面，表示剖析的運算式的類型與值。 `IDebugParsedExpression::EvaluateSync` 使用提供的 SH、 位址和繫結器，將剖析的運算式轉換成實際值，表示`IDebugProperty2`介面。  
  
### <a name="for-example"></a>例如  
 在執行中的程式中叫用中斷點之後，使用者選擇檢視中的變數**快速監看式** 對話方塊。 此對話方塊會顯示變數的名稱，其值，其型別。 通常，使用者可以變更值。  
  
 當**快速監看式** 對話方塊中所示，正在檢查變數的名稱會成為文字，以傳送[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 這會傳回[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件，表示剖析的運算式，在此情況下，該變數。 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)接著會呼叫產生`IDebugProperty2`物件，表示變數的值和類型，以及它的名稱。 就會顯示此資訊。  
  
 如果使用者變更變數的值[SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)呼叫新的值，變更在記憶體中變數的值，使它時，會使用該程式會繼續執行。  
  
 請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)如需詳細資訊，在此程序顯示變數的值。 請參閱[變更區域變數的值](../../extensibility/debugger/changing-the-value-of-a-local.md)如需有關如何變更變數的值。  
  
## <a name="in-this-section"></a>本節內容  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供當 DE 呼叫 EE 所傳遞的引數。  
  
 [主要的運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 說明撰寫 EE，以及評估內容時所需的重要介面。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)   
 [變更區域變數的值](../../extensibility/debugger/changing-the-value-of-a-local.md)
