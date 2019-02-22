---
title: 評估監看式視窗運算式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70ef4cb3bc4ed61166d8ee9b5b89a0518b47290b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033852"
---
# <a name="evaluate-a-watch-window-expression"></a>評估監看式視窗運算式
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 當執行作業會暫停時，Visual Studio 會呼叫偵錯引擎 (DE)，以判斷其監看清單中的每個運算式的目前值。 DE 評估使用的運算式評估工具 (EE)，每個運算式，並在 Visual Studio 會顯示在其值**監看式**視窗。  
  
 以下是監看清單運算式的評估方式的概觀：  
  
1.  Visual Studio 會呼叫 DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)以取得可用來評估運算式的運算式內容。  
  
2.  Visual Studio 會呼叫每個監看清單中，運算式[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)剖析的運算式中轉換的運算式文字。  
  
3.  `IDebugExpressionContext2::ParseText` 呼叫[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)要剖析的文字和產生的實際工作[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)物件。  
  
4.  `IDebugExpressionContext2::ParseText` 會建立[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件，並將`IDebugParsedExpression`到其中的物件。 這個我`DebugExpression2`Visual studio，然後傳回物件。  
  
5.  Visual Studio 呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)評估已剖析的運算式。  
  
6.  `IDebugExpression2::EvaluateSync` 傳遞至呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)來執行實際的評估，並產生[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)會傳回到 Visual Studio 的物件。  
  
7.  Visual Studio 呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)取得運算式，即會顯示在 監看清單的值。  
  
## <a name="parse-then-evaluate"></a>剖析，則評估  
 因為剖析複雜的運算式可能遠超過它評估，評估運算式的程序會分成兩個步驟：1) 剖析的運算式和 2） 評估剖析的運算式。 如此一來，評估可能會發生許多次，但必須一次進行剖析的運算式。 中繼剖析的運算式會傳回從中 EE [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)物件，接著封裝並傳回做為 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。 `IDebugExpression`物件會延後所有評估`IDebugParsedExpression`物件。  
  
> [!NOTE]
>  您不需要遵循此兩步驟程序，即使 Visual Studio 就會認為這方面 EEEE 可以剖析和評估相同的步驟時[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)呼叫 （這是 MyCEE 範例運作方式，例如）。 如果您的語言可以構成複雜的運算式，您可能想要剖析步驟分開評估步驟。 許多監看運算式時，這可以增加效能，在 Visual Studio 偵錯工具會顯示。  
  
## <a name="in-this-section"></a>本節內容  
 [運算式評估的範例實作](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 您可以使用 MyCEE 範例來逐步完成運算式評估的程序。  
  
 [評估監看式運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 說明成功的運算式剖析之後發生的情況。  
  
## <a name="related-sections"></a>相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供偵錯引擎 (DE) 呼叫，運算式評估工具 (EE) 時所傳遞的引數。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)