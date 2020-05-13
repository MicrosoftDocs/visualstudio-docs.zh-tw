---
title: 實現 GetMethod 屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 252d09eee9c69ca75cb46d28dde807f2c500737f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738522"
---
# <a name="implement-getmethodproperty"></a>實現 GetMethod 屬性
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

Visual Studio 呼叫除錯引擎 (DE) [GetDebugProperty,](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)這反過來又調用[GetMethod Property](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)來取得有關堆疊幀上當前方法的資訊。

此執行`IDebugExpressionEvaluator::GetMethodProperty`以下工作:

1. 調用[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md),傳入[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)物件。 符號提供者 (SP) 傳回[IDebugContainerField,](../../extensibility/debugger/reference/idebugcontainerfield.md)表示包含指定位址的方法。

2. 從獲取[IDebugMethodField。](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField`

3. 實例化實現[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面並包含從`IDebugMethodField`SP 返回的物件的類(在此示例`CFieldProperty`中稱為)。

4. 從`IDebugProperty2``CFieldProperty`物件返回介面。

## <a name="managed-code"></a>Managed 程式碼
此示例顯示了託管代碼中的`IDebugExpressionEvaluator::GetMethodProperty`實現。

```csharp
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

## <a name="unmanaged-code"></a>非託管代碼
此示例顯示了非託管代碼中的`IDebugExpressionEvaluator::GetMethodProperty`實現。

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

## <a name="see-also"></a>另請參閱
- [部份變數的樣本實作](../../extensibility/debugger/sample-implementation-of-locals.md)
