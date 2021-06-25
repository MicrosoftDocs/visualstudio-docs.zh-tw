---
title: 運算式評估的範例執行 |Microsoft Docs
description: 瞭解 Visual Studio 如何呼叫 ParseText 來產生 Watch windows 運算式的 IDebugExpression2 物件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de0e052fd42f1603889f7521a1e45e50b0f36eea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902302"
---
# <a name="sample-implementation-of-expression-evaluation"></a>運算式評估的範例執行
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 若為 **監看** 式視窗運算式，Visual Studio 會呼叫 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 來產生 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件。 `IDebugExpressionContext2::ParseText` 具現化運算式評估工具 (EE) 並呼叫 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 來取得 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 物件。

 會 `IDebugExpressionEvaluator::Parse` 執行下列工作：

1. [僅限 c + +]剖析運算式以找出錯誤。

2. 具現化在此範例中呼叫的類別 (`CParsedExpression`) 會執行 `IDebugParsedExpression` 介面，並在類別中儲存要剖析的運算式。

3. 傳回 `IDebugParsedExpression` 物件的介面 `CParsedExpression` 。

> [!NOTE]
> 在接下來和 MyCEE 範例中的範例中，運算式評估工具不會將剖析與評估分開。

## <a name="managed-code"></a>Managed 程式碼
 下列程式碼示範如何 `IDebugExpressionEvaluator::Parse` 在 managed 程式碼中執行。 此版本的方法會將剖析延遲至 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ，因為剖析程式碼也會同時進行評估 (請參閱 [評估監看式運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)) 。

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>非受控碼
下列程式碼是 `IDebugExpressionEvaluator::Parse` 在非受控碼中的實作為。 這個方法會呼叫 helper 函式， `Parse` 以剖析運算式並檢查是否有錯誤，但這個方法會忽略產生的值。 正式評估會延後至 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ，在評估運算式時剖析運算式 (請參閱 [評估監看式運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)) 。

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [評估監看式視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [評估監看式運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)
