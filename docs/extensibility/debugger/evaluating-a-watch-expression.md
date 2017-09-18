---
title: "監看式運算式評估 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式評估、 監看式運算式"
  - "監看運算式"
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 監看式運算式評估
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 Visual Studio 即可顯示監看式運算式的值時，它會呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 接著呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 這會產生 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，其中包含的值和運算式的類型。  
  
 在此實作中的 `IDebugParsedExpression::EvaluateSync`, ，剖析並同時評估運算式。 這個實作會執行下列工作:  
  
1.  剖析，並評估運算式，以產生一般的物件保留值和型別。 在 C\# 中，這以表示 `object` 雖然 c \+ \+ 中，以表示為 `VARIANT`。  
  
2.  具現化類別 \(稱為 `CValueProperty` 在此範例中\) 來實作 `IDebugProperty2` 介面，並將傳回值儲存在類別中。  
  
3.  傳回 `IDebugProperty2` 介面從 `CValueProperty` 物件。  
  
## Managed 程式碼  
 這是實作 `IDebugParsedExpression::EvaluateSync` managed 程式碼中。 Helper 方法 `Tokenize` 剖析成剖析樹狀目錄的運算式。 Helper 函式 `EvalToken` 轉換為值的語彙基元。 Helper 函式 `FindTerm` 遞迴周遊剖析樹狀結構中，呼叫 `EvalToken` 代表值和套用任何作業 \(加或乘\) 在運算式中每一個節點。  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT EvaluateSync( uint evalFlags, uint timeout, IDebugSymbolProvider provider, IDebugAddress address, IDebugBinder binder, string resultType, out IDebugProperty2 result) { HRESULT retval = COM.S_OK; this.evalFlags = evalFlags; this.timeout = timeout; this.provider = provider; this.address = address; this.binder = binder; this.resultType = resultType; try { IDebugField field = null; // Tokenize, then parse. tokens = Tokenize(expression); result = new CValueProperty( expression, (int) FindTerm(EvalToken(tokens[0], out field),1), field, binder); } catch (ParseException) { result = new CValueProperty(expression, "Huh?"); retval = COM.E_INVALIDARG; } return retval; } } }  
```  
  
## Unmanaged 程式碼  
 這是實作 `IDebugParsedExpression::EvaluateSync` unmanaged 程式碼中。 Helper 函式 `Evaluate` 剖析並評估的運算式，傳回 `VARIANT` 保留產生的值。 Helper 函式 `VariantValueToProperty` 套組 `VARIANT` 到 `CValueProperty` 物件。  
  
```  
[C++] STDMETHODIMP CParsedExpression::EvaluateSync( in  DWORD                 evalFlags, in  DWORD                 dwTimeout, in  IDebugSymbolProvider* pprovider, in  IDebugAddress*        paddress, in  IDebugBinder*         pbinder, in  BSTR                  bstrResultType, out IDebugProperty2**     ppproperty ) { // dwTimeout parameter is ignored in this implementation. if (pprovider == NULL) return E_INVALIDARG; if (paddress == NULL) return E_INVALIDARG; if (pbinder == NULL) return E_INVALIDARG; if (ppproperty == NULL) return E_INVALIDARG; else *ppproperty = 0; HRESULT hr; VARIANT value; BSTR    bstrErrorMessage = NULL; hr = ::Evaluate( pprovider, paddress, pbinder, m_expr, &bstrErrorMessage, &value ); if (hr != S_OK) { if (bstrErrorMessage == NULL) return hr; //we can display better messages ourselves. HRESULT hrLocal = S_OK; VARIANT varType; VARIANT varErrorMessage; VariantInit( &varType ); VariantInit( &varErrorMessage ); varErrorMessage.vt      = VT_BSTR; varErrorMessage.bstrVal = bstrErrorMessage; CValueProperty* valueProperty = new CValueProperty(); if (valueProperty != NULL) { hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage); if (SUCCEEDED(hrLocal)) { hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2, reinterpret_cast<void**>(ppproperty) ); } } VariantClear(&varType); VariantClear(&varErrorMessage); //frees BSTR if (!valueProperty) return hr; valueProperty->Release(); if (FAILED(hrLocal)) return hr; } else { if (bstrErrorMessage != NULL) SysFreeString(bstrErrorMessage); hr = VariantValueToProperty( pprovider, paddress, pbinder, m_radix, m_expr, value, ppproperty ); VariantClear(&value); if (FAILED(hr)) return hr; } return S_OK; }  
```  
  
## 請參閱  
 [監看式\] 視窗中的運算式評估](../Topic/Evaluating%20a%20Watch%20Window%20Expression.md)   
 [運算式評估的實作範例](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)