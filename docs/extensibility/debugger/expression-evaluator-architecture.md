---
title: 運算式評估器體系結構 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738705"
---
# <a name="expression-evaluator-architecture"></a>運算式賦值器架構結構
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 將專有語言整合到 Visual Studio 調試套件中意味著必須設置所需的運算式賦值器 (EE) 介面,並調用通用語言執行時符號提供者 (SP) 和粘合劑介面。 SP 和活頁夾物件以及當前執行位址是計算表達式的上下文。 這些介面產生和使用的資訊代表了 EE 體系結構中的關鍵概念。

## <a name="overview"></a>概觀

### <a name="parse-the-expression"></a>解析運算式
 除錯程式時,表達式的計算原因有很多,但總是在正在調試的程式在斷點停止時(用戶放置的斷點或由異常引起的斷點)。 此時,Visual Studio 從調試引擎 (DE) 獲取一個堆疊幀,由[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面表示。 然後,視覺化工作室調用[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)來獲取[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 此介面表示可以計算表達式的上下文;[分析文本](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)是評估過程的入口點。 在此之前,所有介面都由 DE 實現。

 調用`IDebugExpressionContext2::ParseText`時,DE 實例化與發生斷點的源檔的語言關聯的 EE(此時 DE 還會實例化 SH)。 EE 由[IDebugExpression 評估器](../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面表示。 然後,DE 調用[Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)將運算式(文本形式)轉換為已解析的運算式,以便進行計算。 此解析表示式由[IDebugParsed 運算式](../../extensibility/debugger/reference/idebugparsedexpression.md)介面表示。 表達式通常被解析,此時不計算。

 DE 建立一個[實作 IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面`IDebugParsedExpression`的物件,`IDebugExpression2`將物件放入物件`IDebugExpression2`,並`IDebugExpressionContext2::ParseText`從中傳回 該物件 。

### <a name="evaluate-the-expression"></a>計算運算式
 Visual Studio 調用[評估同步](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[評估 Async](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)以評估解析的運算式。 這兩種方法都調用[EvaluateSync(](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)`IDebugExpression2::EvaluateSync`立即調用方法`IDebugExpression2::EvaluateAsync`,同時 通過後台線程調用方法),以評估解析的表達式並返回表示解析表達式的值和類型的[IDebug Property2](../../extensibility/debugger/reference/idebugproperty2.md)介面。 `IDebugParsedExpression::EvaluateSync`使用提供的 SH、位址和活頁夾將解析的運算式轉換為實際值,該值`IDebugProperty2`由介面表示。

### <a name="for-example"></a>例如：
 在正在運行的程式中命中斷點後,用戶選擇在**QuickWatch**對話框中查看變數。 此對話框顯示變數的名稱、值及其類型。 使用者通常可以更改該值。

 顯示 **'快速觀察'** 對話框時, 檢查的變數名稱會作為文字傳送[到 ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 這將返回表示解析表達式(本例中為變數)的[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。 然後調用[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)`IDebugProperty2`以生成 表示變數的值和類型以及其名稱的物件。 顯示的是此資訊。

 如果使用者更改變量的值,則使用新值調用[SetValueAsString,](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)該值會更改記憶體中變數的值,以便在程式繼續運行時使用它。

 有關顯示變數值的此過程的更多詳細資訊,請參閱[顯示局部變數](../../extensibility/debugger/displaying-locals.md)。 有關如何更改變量值的更多詳細資訊[,請參閱變更本地值](../../extensibility/debugger/changing-the-value-of-a-local.md)。

## <a name="in-this-section"></a>本節內容
 [評估上下文](../../extensibility/debugger/evaluation-context.md)提供 DE 呼叫 EE 時傳遞的參數。

 [鍵運算式賦值器介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)描述編寫 EE 時所需的關鍵介面以及評估上下文。

## <a name="see-also"></a>另請參閱
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [顯示本地變數](../../extensibility/debugger/displaying-locals.md)
- [變更本地值](../../extensibility/debugger/changing-the-value-of-a-local.md)
