---
title: 評估監看式運算式 |Microsoft Docs
description: 瞭解當 Visual Studio 準備好顯示 watch 運算式的值時，如何使用 EvaluateSync。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 84e3b020da8d7fc6e4d7f3be89eaa50cd59c704e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851331"
---
# <a name="evaluate-a-watch-expression"></a>評估監看式運算式
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

當 Visual Studio 準備好顯示 watch 運算式的值時，它會呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)，然後再呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 此進程會產生 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，其中包含運算式的值和類型。

在的這個執行中 `IDebugParsedExpression::EvaluateSync` ，會同時剖析運算式並進行評估。 這項實行會執行下列工作：

1. 剖析並評估運算式，以產生保存值和其類型的泛型物件。 在 c # 中，這在 c + + 中是以時程表示 `object` ，這是以表示 `VARIANT` 。

2. 具現化在此範例中呼叫的類別 (`CValueProperty`) 這個範例會執行 `IDebugProperty2` 介面，並在類別中儲存要傳回的值。

3. 傳回 `IDebugProperty2` 物件的介面 `CValueProperty` 。

## <a name="managed-code"></a>Managed 程式碼
這是 `IDebugParsedExpression::EvaluateSync` 在 managed 程式碼中的實作為。 Helper 方法會將 `Tokenize` 運算式剖析為剖析樹狀結構。 Helper 函式會 `EvalToken` 將 token 轉換成值。 Helper 函式會 `FindTerm` 以遞迴方式遍歷剖析樹狀結構， `EvalToken` 並針對代表值的每個節點呼叫，並套用任何作業 (運算式中的加法或減法) 。

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>非受控碼
這是 `IDebugParsedExpression::EvaluateSync` 在非受控碼中的實作為。 Helper 函式會剖析 `Evaluate` 並評估運算式，並傳回 `VARIANT` 包含所產生值的。 Helper 函式會 `VariantValueToProperty` 將 `VARIANT` 轉換成 `CValueProperty` 物件。

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>另請參閱
- [評估監看式視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [運算式評估的範例執行](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
