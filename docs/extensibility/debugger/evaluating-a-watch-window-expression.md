---
title: 評估監看式視窗運算式 |Microsoft Docs
description: 瞭解當執行暫停時，Visual Studio 如何呼叫 debug engine 來判斷其監看清單中每個運算式的目前值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 34367b836e766754ce5e274698eb4f5a5d407760
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840609"
---
# <a name="evaluate-a-watch-window-expression"></a>評估監看式視窗運算式
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 當執行暫停時，Visual Studio 會呼叫 debug engine (DE) 以判斷其監看清單中每個運算式的目前值。 DE 會使用運算式評估工具 (EE) 來評估每個運算式，並 Visual Studio 在 [ **監看** 式] 視窗中顯示其值。

 以下概述監看清單運算式的評估方式：

1. Visual Studio 會呼叫 DE 的 [GetExpressionCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) ，以取得可用於評估運算式的運算式內容。

2. 對於監看清單中的每個運算式，Visual Studio 會呼叫 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ，將運算式文字轉換成剖析的運算式。

3. `IDebugExpressionContext2::ParseText` 呼叫 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 來執行剖析文字的實際工作，並產生 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 物件。

4. `IDebugExpressionContext2::ParseText` 建立 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件，並將 `IDebugParsedExpression` 物件放入其中。 然後此 I `DebugExpression2` 物件會傳回 Visual Studio。

5. Visual Studio 會呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 來評估剖析的運算式。

6. `IDebugExpression2::EvaluateSync` 將呼叫傳遞給 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ，以進行實際的評估並產生傳回給 Visual Studio 的 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件。

7. Visual Studio 會呼叫 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 來取得接著顯示在監看式清單中的運算式值。

## <a name="parse-then-evaluate"></a>剖析然後評估
 由於剖析複雜運算式所需的時間可能比評估複雜運算式來得久，因此評估運算式的程式分為兩個步驟： 1) 剖析運算式，2) 評估剖析的運算式。 如此一來，評估可能會發生多次，但運算式只需要剖析一次。 中繼剖析的運算式會從 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 物件中的 EE 傳回，該物件接著會以 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件的形式從 DE 封裝並傳回。 物件會將 `IDebugExpression` 所有評估延遲到 `IDebugParsedExpression` 物件。

> [!NOTE]
> 即使 Visual Studio 採用這個程式，EE 仍不需要遵守這個兩步驟的程式;當呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 時，EE 可以剖析和評估相同的步驟 (這是 MyCEE 範例的運作方式，例如) 。 如果您的語言可以形成複雜的運算式，您可能會想要將剖析步驟與評估步驟分開。 當顯示許多監看式運算式時，這可以提升 Visual Studio 偵錯工具的效能。

## <a name="in-this-section"></a>本節內容
 [運算式評估的範例執行](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) 使用 MyCEE 範例逐步執行運算式評估的處理常式。

 [評估監看式運算式](../../extensibility/debugger/evaluating-a-watch-expression.md) 說明成功運算式剖析之後會發生什麼事。

## <a name="related-sections"></a>相關章節
 [評估內容](../../extensibility/debugger/evaluation-context.md) 提供當 debug engine (DE) 呼叫運算式評估工具 (EE) 時所傳遞的引數。

## <a name="see-also"></a>另請參閱
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
