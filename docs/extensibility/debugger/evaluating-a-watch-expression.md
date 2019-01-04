---
title: 評估監看式運算式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14635c18fe772df566cdd16a285816ece0cdf485
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945008"
---
# <a name="evaluate-a-watch-expression"></a>評估監看式運算式
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 Visual Studio 即可顯示 監看式運算式的值時，它會呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)，接著呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 此程序會產生[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件，其中包含的值和運算式的類型。  
  
 在此實作中的`IDebugParsedExpression::EvaluateSync`，剖析並同時評估運算式。 此實作會執行下列工作：  
  
1.  會剖析並評估運算式，以產生可儲存值和其類型的泛型物件。 在 C# 中，這表示為`object`在 c + +，這表示為`VARIANT`。  
  
2.  具現化類別 (稱為`CValueProperty`在此範例中) 可實`IDebugProperty2`介面，並儲存在類別中要傳回的值。  
  
3.  傳回`IDebugProperty2`介面從`CValueProperty`物件。  
  
## <a name="managed-code"></a>Managed 程式碼  
 這是實作`IDebugParsedExpression::EvaluateSync`managed 程式碼中。 Helper 方法`Tokenize`剖析成剖析樹狀目錄的運算式。 Helper 函式`EvalToken`將語彙基元轉換成的值。 Helper 函式`FindTerm`以遞迴方式周遊剖析樹狀目錄中，呼叫`EvalToken`表示值和套用任何作業 （加法或減法） 的運算式中每一個節點。  
  
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
  
## <a name="unmanaged-code"></a>Unmanaged 程式碼  
 這是實作`IDebugParsedExpression::EvaluateSync`unmanaged 程式碼中。 Helper 函式`Evaluate`剖析並評估的運算式，傳回`VARIANT`保留所產生的值。 Helper 函式`VariantValueToProperty`配套`VARIANT`到`CValueProperty`物件。  
  
```cpp  
[C++]  
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
 [評估監看式視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [運算式評估的範例實作](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)