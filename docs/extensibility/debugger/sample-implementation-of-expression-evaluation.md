---
title: "範例的運算式評估實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ca872421d20d1d1a85cb2c5db621de28adee356d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="sample-implementation-of-expression-evaluation"></a>運算式評估的實作範例
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 如**監看式**視窗運算式，Visual Studio 會呼叫[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)產生[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。 `IDebugExpressionContext2::ParseText`具現化的運算式評估工具 (EE) 和呼叫[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)取得[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)物件。  
  
 這項實作`IDebugExpressionEvaluator::Parse`會執行下列工作：  
  
1.  [只有 c + +]剖析運算式，若要尋找的錯誤。  
  
2.  具現化類別 (稱為`CParsedExpression`在此範例中)，用來實作`IDebugParsedExpression`介面，並儲存在類別中，無法剖析運算式。  
  
3.  傳回`IDebugParsedExpression`介面從`CParsedExpression`物件。  
  
> [!NOTE]
>  在接下來的範例和 MyCEE 範例中，運算式評估工具不會分開評估剖析。  
  
## <a name="managed-code"></a>Managed 程式碼  
 這是實作`IDebugExpressionEvaluator::Parse`managed 程式碼中。 請注意，這個版本的方法會延遲到剖析[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)剖析的程式碼也會同時評估如下 (請參閱[監看式運算式評估](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
  
## <a name="unmanaged-code"></a>Unmanaged 程式碼  
 這是實作`IDebugExpressionEvaluator::Parse`unmanaged 程式碼中。 這個方法會呼叫 helper 函式， `Parse`、 剖析運算式，然後檢查是否發生錯誤，但這個方法會忽略所產生的值。 型式的評估會延後至[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)時就會評估其中剖析運算式 (請參閱[監看式運算式評估](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
 [監看式視窗運算式評估](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [評估監看運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)
