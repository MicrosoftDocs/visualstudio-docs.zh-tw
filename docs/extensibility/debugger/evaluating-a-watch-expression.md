---
title: 評估監視運算式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738850"
---
# <a name="evaluate-a-watch-expression"></a>監控監視運算式
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

當 Visual Studio 準備好顯示手錶表示式的值時,它呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md),這反過來又呼叫[評估同步](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 此過程生成包含表達式的值和類型的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件。

在此實現`IDebugParsedExpression::EvaluateSync`中 ,將同時解析和計算表達式。 此執行以下工作:

1. 分析並計算表達式以生成保存該值及其類型的泛型物件。 在 C# 中,`object`這表示 為 C++`VARIANT`中的一段時間,這 表示為 。

2. 實例化實現`IDebugProperty2`介面並在類中`CValueProperty`存儲 要返回的值的類(在此示例中稱為)。

3. 從`IDebugProperty2``CValueProperty`物件返回介面。

## <a name="managed-code"></a>Managed 程式碼
這是`IDebugParsedExpression::EvaluateSync`託管代碼的實現。 説明器方法`Tokenize`將表達式解析為解析樹。 説明器函數`EvalToken`將令牌轉換為值。 説明器函數`FindTerm`遞歸地遍歷解析樹,調`EvalToken`用 表示值的每個節點,並在運算式中應用任何操作(添加或減法)。

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

## <a name="unmanaged-code"></a>非託管代碼
這是非託管代碼的`IDebugParsedExpression::EvaluateSync`實現。 説明器函數`Evaluate`解析和計算表達式,`VARIANT`返回保留結果值。 說明器函數`VariantValueToProperty`將`VARIANT`捆綁到`CValueProperty`物件中 。

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
- [監控監視視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [運算式樣本實作](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
