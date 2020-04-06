---
title: 監控監視視窗運算式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738847"
---
# <a name="evaluate-a-watch-window-expression"></a>監控監視視窗運算式
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 當執行暫停時,Visual Studio 調用調試引擎 (DE) 以確定其監視清單中每個表達式的當前值。 DE 使用運算式賦值器 (EE) 計算每個運算式,Visual Studio 在 **「監視」** 視窗中顯示其值。

 以下是如何計算觀察清單表示式的概述:

1. Visual Studio 調用 DE 的[GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)來取得可用於計算運算式運算式運算式運算式相片。

2. 對於監視清單中的每個運算式,Visual Studio 呼叫[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)將表示式文本轉換為已解析的運算式。

3. `IDebugExpressionContext2::ParseText`呼叫[Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)執行分析文字的實際工作並生成[IDebugParsed 運算](../../extensibility/debugger/reference/idebugparsedexpression.md)式物件。

4. `IDebugExpressionContext2::ParseText`創建[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)`IDebugParsedExpression`物件並將 物件放入其中。 然後,`DebugExpression2`此 I 物件將返回到視覺工作室。

5. 可視化工作室調用[評估同步](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)來評估解析的運算式。

6. `IDebugExpression2::EvaluateSync`將調用傳遞到[評估同步](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)以執行實際評估,並生成返回到 Visual Studio 的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件。

7. Visual Studio 調用[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)以獲取表達式的值,然後顯示在監視清單中。

## <a name="parse-then-evaluate"></a>分析然後評估
 由於分析複雜表達式可能比計算它需要更長的時間,因此計算表達式的過程分為兩個步驟:1 解析表達式,2) 計算解析表達式。 這樣,計算可以發生多次,但表達式只需要分析一次。 中間解析表示式從[IDebugParsedExpression 運算式](../../extensibility/debugger/reference/idebugparsedexpression.md)物件的 EE 傳回,該物件依次封裝並從 DE 作為[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件返回。 物件`IDebugExpression`會將所有計算延遲`IDebugParsedExpression`到 物件。

> [!NOTE]
> 即使 Visual Studio 假定這一點,EE 也不必遵守此兩步過程;調用[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)時,EE 可以在同一步驟中分析和評估(例如,MyCEE 示例的工作原理)。 如果語言可以形成複雜的表達式,則可能需要將解析步驟與計算步驟分開。 當顯示許多監視運算式時,這可以提高 Visual Studio 調試器的性能。

## <a name="in-this-section"></a>本節內容
 [運算式樣本實作](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)使用 MyCEE 範例逐步完成表達式評估過程。

 [監控監視運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)解釋成功解析表達式后發生的情況。

## <a name="related-sections"></a>相關章節
 [評估上下文](../../extensibility/debugger/evaluation-context.md)提供調試引擎 (DE) 調用表示式賦值器 (EE) 時傳遞的參數。

## <a name="see-also"></a>另請參閱
 [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
