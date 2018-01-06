---
title: "評估 監看式視窗運算式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb109fd91e4c295bf372b14e26bc2a75c3be6b1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-a-watch-window-expression"></a>監看式視窗運算式評估
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 當執行暫停時，Visual Studio 會呼叫偵錯引擎 (DE) 來判斷其監看清單 中的每個運算式的目前值。 DE 評估使用的運算式評估工具 (EE)，每個運算式，並顯示其值中的，Visual Studio**監看式**視窗。  
  
 以下是如何評估監看清單運算式的概觀：  
  
1.  Visual Studio 會呼叫 DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)以取得可用來評估運算式，運算式內容。  
  
2.  在 [監看式] 清單中每一個運算式，Visual Studio 會呼叫[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)將運算式文字轉換成剖析的運算式。  
  
3.  `IDebugExpressionContext2::ParseText`呼叫[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)要剖析的文字和產生的實際工作[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)物件。  
  
4.  `IDebugExpressionContext2::ParseText`建立[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件並將`IDebugParsedExpression`到其中的物件。 此我`DebugExpression2`物件傳回至 Visual Studio。  
  
5.  Visual Studio 呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)評估剖析的運算式。  
  
6.  `IDebugExpression2::EvaluateSync`傳遞至呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)執行實際的評估，並產生[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)會傳回到 Visual Studio 的物件。  
  
7.  Visual Studio 呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)取得即會顯示在 監看清單運算式的值。  
  
## <a name="parse-then-evaluate"></a>剖析，然後評估  
 剖析複雜運算式可以取得其長度遠超過進行評估，因為運算式的評估程序會分成兩個步驟： 1） 剖析運算式，以及 2） 評估剖析的運算式。 如此一來，評估可能會發生多次，但必須一次剖析運算式。 中繼剖析的運算式會傳回從中 EE [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)物件，接著封裝並傳回為 DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。 `IDebugExpression`物件延後所有評估`IDebugParsedExpression`物件。  
  
> [!NOTE]
>  不需要遵守此兩步驟程序，即使 Visual Studio 會假設; EEEE 可以剖析和評估相同的步驟時[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)稱為 （這是 MyCEE 範例的運作方式，例如）。 如果您的語言可以形成複雜的運算式，您可能想要剖析步驟分開評估步驟。 許多監看運算式時，這可以增加效能，Visual Studio 偵錯工具中的顯示。  
  
## <a name="in-this-section"></a>本節內容  
 [運算式評估的實作範例](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 若要逐步執行的運算式評估程序使用 MyCEE 範例。  
  
 [評估監看運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 說明成功的運算式剖析後的動作。  
  
## <a name="related-sections"></a>相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 提供偵錯引擎 (DE) 呼叫運算式評估工具 (EE) 時，會傳遞的引數。  
  
## <a name="see-also"></a>請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)