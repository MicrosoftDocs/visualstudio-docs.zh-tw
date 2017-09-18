---
title: "運算式評估的實作範例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算試評估工具"
  - "偵錯的 [偵錯 SDK]，運算式評估工具"
  - "運算式評估、 範例"
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 運算式評估的實作範例
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 如 **監看式** 視窗運算式，Visual Studio 會呼叫 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 產生 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件。`IDebugExpressionContext2::ParseText` 具現化的運算式評估工具 \(EE\) 並呼叫 [剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 取得 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 物件。  
  
 這項實作的 `IDebugExpressionEvaluator::Parse` 會執行下列工作:  
  
1.  \[只有 c \+ \+\]剖析運算式，尋找錯誤。  
  
2.  具現化類別 \(稱為 `CParsedExpression` 在此範例中\) 來實作 `IDebugParsedExpression` 介面，並儲存在類別中，運算式才能進行剖析。  
  
3.  傳回 `IDebugParsedExpression` 介面從 `CParsedExpression` 物件。  
  
> [!NOTE]
>  在接下來的範例和 MyCEE 範例中，運算式評估工具不會分隔求值的剖析。  
  
## Managed 程式碼  
 這是實作 `IDebugExpressionEvaluator::Parse` managed 程式碼中。 請注意，這個版本的方法會延遲到剖析 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 為剖析的程式碼也會評估一次 \(請參閱 [監看式運算式評估](../../extensibility/debugger/evaluating-a-watch-expression.md)\)。  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT Parse( string                 expression, uint                   parseFlags, uint                   radix, out string                 errorMessage, out uint                   errorPosition, out IDebugParsedExpression parsedExpression) { errorMessage = ""; errorPosition = 0; parsedExpression = new CParsedExpression(parseFlags, radix, expression); return COM.S_OK; } } }  
```  
  
## Unmanaged 程式碼  
 這是實作 `IDebugExpressionEvaluator::Parse` unmanaged 程式碼中。 這個方法會呼叫 helper 函式， `Parse`, ，若要剖析的運算式和檢查是否發生錯誤，但這個方法會忽略所產生的值。 正式的評估會延後到 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 時進行評估，其中剖析運算式 \(請參閱 [監看式運算式評估](../../extensibility/debugger/evaluating-a-watch-expression.md)\)。  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse( in    LPCOLESTR                 pszExpression, in    PARSEFLAGS                flags, in    UINT                      radix, out   BSTR                     *pbstrErrorMessages, inout UINT                     *perrorCount, out   IDebugParsedExpression  **ppparsedExpression ) { if (pbstrErrorMessages == NULL) return E_INVALIDARG; else *pbstrErrormessages = 0; if (pparsedExpression == NULL) return E_INVALIDARG; else *pparsedExpression = 0; if (perrorCount == NULL) return E_INVALIDARG; HRESULT hr; // Look for errors in the expression but ignore results hr = ::Parse( pszExpression, pbstrErrorMessages ); if (hr != S_OK) return hr; CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression ); if (!pparsedExpr) return E_OUTOFMEMORY; hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression, reinterpret_cast<void**>(ppparsedExpression) ); pparsedExpr->Release(); return hr; }  
```  
  
## 請參閱  
 [監看式\] 視窗中的運算式評估](../Topic/Evaluating%20a%20Watch%20Window%20Expression.md)   
 [監看式運算式評估](../../extensibility/debugger/evaluating-a-watch-expression.md)