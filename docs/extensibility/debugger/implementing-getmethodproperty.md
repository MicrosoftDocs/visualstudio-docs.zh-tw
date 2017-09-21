---
title: "實作 GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMethodProperty 方法"
  - "IDebugExpressionEvaluator2 屬性"
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 實作 GetMethodProperty
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 Visual Studio 偵錯引擎 \(DE\) 會呼叫 [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), ，接著呼叫 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 以取得有關目前方法的堆疊框架。  
  
 這項實作的 `IDebugExpressionEvaluator::GetMethodProperty` 會執行下列工作︰  
  
1.  呼叫 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), ，並傳入 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 物件。 符號提供者 \(SP\) 會傳回 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 代表包含指定的位址的方法。  
  
2.  取得 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 從 `IDebugContainerField`。  
  
3.  具現化類別 \(稱為 `CFieldProperty` 在此範例中\) 來實作 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面，並包含 `IDebugMethodField` SP 從傳回的物件  
  
4.  傳回 `IDebugProperty2` 介面從 `CFieldProperty` 物件。  
  
## Managed 程式碼  
 這個範例會示範實作 `IDebugExpressionEvaluator::GetMethodProperty` managed 程式碼中。  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## Unmanaged 程式碼  
 這個範例會示範實作 `IDebugExpressionEvaluator::GetMethodProperty` unmanaged 程式碼中。  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## 請參閱  
 [範例實作的區域變數](../../extensibility/debugger/sample-implementation-of-locals.md)