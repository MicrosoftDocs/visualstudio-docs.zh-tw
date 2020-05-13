---
title: 運算式評估的範例實現 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713104"
---
# <a name="sample-implementation-of-expression-evaluation"></a>運算式樣本實作
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 對於**監視**視窗運算式,Visual Studio 調用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)生成[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。 `IDebugExpressionContext2::ParseText`實例化運算式賦值器 (EE) 並呼叫[Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)取得[IDebugParsed 運算](../../extensibility/debugger/reference/idebugparsedexpression.md)式物件。

 執行`IDebugExpressionEvaluator::Parse`以下工作:

1. [僅C++]分析表達式以查找錯誤。

2. 實例化運行`IDebugParsedExpression`介面並在類中`CParsedExpression`存儲 要解析的表達式的類(在此示例中稱為)。

3. 從`IDebugParsedExpression``CParsedExpression`物件返回介面。

> [!NOTE]
> 在 MyCEE 範例之後和其中的範例中,表達式賦值器不會將分析與評估分開。

## <a name="managed-code"></a>Managed 程式碼
 以下代碼顯示了託管代碼中的`IDebugExpressionEvaluator::Parse`實現。 此版本的方法將解析延遲到[EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)因為用於分析的代碼也會同時計算(請參閱[評估 Watch 運算式](../../extensibility/debugger/evaluating-a-watch-expression.md))。

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

## <a name="unmanaged-code"></a>非託管代碼
以下代碼是在非託管代碼`IDebugExpressionEvaluator::Parse`中的實現。 此方法調用説明器函數`Parse`, 以解析表示式並檢查錯誤,但此方法忽略生成的值。 正式計算延遲到[評估同步](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md),在計算表達式時解析表達式(請參閱[評估觀察表達式](../../extensibility/debugger/evaluating-a-watch-expression.md))。

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
- [檢視「監視」視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [監控監視運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)
