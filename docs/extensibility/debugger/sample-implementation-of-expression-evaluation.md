---
title: 範例運算式評估的實作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aac8e120880ba33b1479bd43ae43f5449c9e97d1
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251107"
---
# <a name="sample-implementation-of-expression-evaluation"></a>運算式評估的範例實作
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 針對**監看式** 視窗的運算式時，Visual Studio 會呼叫[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)產生[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。 `IDebugExpressionContext2::ParseText` 具現化的運算式評估工具 (EE) 和呼叫[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)若要取得[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)物件。  
  
 `IDebugExpressionEvaluator::Parse`會執行下列工作：  
  
1.  [只有 c + +]剖析的運算式，若要尋找的錯誤。  
  
2.  具現化類別 (稱為`CParsedExpression`在此範例中) 執行`IDebugParsedExpression`介面，並儲存在類別中，運算式才能進行剖析。  
  
3.  傳回`IDebugParsedExpression`介面從`CParsedExpression`物件。  
  
> [!NOTE]
>  在接下來的範例和 MyCEE 範例中，運算式評估工具不會分開評估剖析。  
  
## <a name="managed-code"></a>Managed 程式碼  
 下列程式碼示範如何實作`IDebugExpressionEvaluator::Parse`managed 程式碼中。 這個版本的方法會延後到剖析[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)當剖析的程式碼也會評估一次 (請參閱[評估 監看運算式](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
下列程式碼是實作`IDebugExpressionEvaluator::Parse`unmanaged 程式碼中。 這個方法會呼叫 helper 函式， `Parse`、 要剖析的運算式和檢查是否發生錯誤，但這個方法會忽略所產生的值。 型式的評估會延後到[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)時就會評估，其中剖析運算式 (請參閱[評估 監看運算式](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
 [評估監看式視窗運算式](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [評估監看式運算式](../../extensibility/debugger/evaluating-a-watch-expression.md)