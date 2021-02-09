---
title: 運算式評估工具架構 |Microsoft Docs
description: 瞭解如何將專屬語言整合至 Visual Studio 的 debug 封裝，包括運算式評估工具和符號提供者/系結器介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac81d386f0e1104879701faba230d5384259fa25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921411"
---
# <a name="expression-evaluator-architecture"></a>運算式評估工具架構
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 將專屬語言整合至 Visual Studio 的 debug 封裝中，表示您必須設定必要的運算式評估工具 (EE) 介面，並呼叫通用語言執行時間符號提供者 (SP) 和系結器介面。 SP 和系結器物件（以及目前的執行位址）是評估運算式的內容。 這些介面產生和取用的資訊代表 EE 架構中的重要概念。

## <a name="overview"></a>概觀

### <a name="parse-the-expression"></a>剖析運算式
 當您在偵錯工具時，會評估運算式的原因有很多，但一律會在正在進行偵錯工具的中斷點停止時 (使用者所放置的中斷點，或是由例外狀況) 所造成的中斷點。 當 Visual Studio 從 debug engine 取得堆疊框架（以 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 介面表示）時， (DE) 。 Visual Studio 接著會呼叫 [GetExpressionCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 來取得 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。 此介面代表可在其中評估運算式的內容。 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 是評估流程的進入點。 直到目前為止，所有介面都是由 DE 來執行。

 當 `IDebugExpressionContext2::ParseText` 呼叫時，會將與來源檔案的語言相關聯的 EE 具現化，而該來源檔案的中斷點發生在 (也會在此時將 SH 具現化) 。 EE 會以 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) 介面表示。 然後，會呼叫 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 以將文字) 形式的運算式 (轉換成剖析的運算式，以準備進行評估。 這個剖析的運算式會以 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 介面表示。 此運算式通常會進行剖析，而不會在此時進行評估。

 DE 會建立一個物件，該物件會執行 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 介面、將 `IDebugParsedExpression` 物件放入 `IDebugExpression2` 物件，並 `IDebugExpression2` 從傳回物件 `IDebugExpressionContext2::ParseText` 。

### <a name="evaluate-the-expression"></a>評估運算式
 Visual Studio 會呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 或 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 來評估剖析的運算式。 這兩種方法都會[](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)呼叫 EvaluateSync `IDebugExpression2::EvaluateSync` ， (立即呼叫方法，而 `IDebugExpression2::EvaluateAsync` 透過背景執行緒呼叫方法) 來評估剖析的運算式，並傳回代表已剖析運算式之值和類型的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。 `IDebugParsedExpression::EvaluateSync` 使用提供的 SH、address 和系結器，將剖析的運算式轉換為實際值（由介面表示） `IDebugProperty2` 。

### <a name="for-example"></a>例如：
 在執行程式中叫用中斷點之後，使用者選擇在 [ **快速** 監看式] 對話方塊中查看變數。 此對話方塊會顯示變數的名稱、其值和類型。 使用者通常可以變更此值。

 當顯示 [ **快速** 監看式] 對話方塊時，所檢查之變數的名稱會以文字的形式傳送至 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)。 這會傳回 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件，代表已剖析的運算式，在此案例中為變數。 接著會呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ，以產生 `IDebugProperty2` 代表變數值和類型以及其名稱的物件。 這是所顯示的資訊。

 如果使用者變更變數的值，則會使用新的值來呼叫 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) ，這會變更記憶體中的變數值，以便在程式繼續執行時使用。

 如需顯示變數值的此程式的詳細資訊，請參閱 [顯示區域變數](../../extensibility/debugger/displaying-locals.md) 。 如需變更變數值的詳細資訊，請參閱 [變更本機的值](../../extensibility/debugger/changing-the-value-of-a-local.md) 。

## <a name="in-this-section"></a>本節內容
 [評估內容](../../extensibility/debugger/evaluation-context.md) 提供當 DE 呼叫 EE 時所傳遞的引數。

 索引[鍵運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)描述撰寫 EE 時所需要的重要介面，以及評估內容。

## <a name="see-also"></a>另請參閱
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)
- [變更本機的值](../../extensibility/debugger/changing-the-value-of-a-local.md)
