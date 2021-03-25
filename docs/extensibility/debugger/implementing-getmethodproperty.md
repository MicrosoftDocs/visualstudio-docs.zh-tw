---
title: 執行 GetMethodProperty |Microsoft Docs
description: 瞭解 Visual Studio 如何使用 debug 引擎的 GetDebugProperty，取得堆疊框架上目前方法的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0a52174e05d7203d5bc35e43df8886e23ea7296
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059820"
---
# <a name="implement-getmethodproperty"></a>執行 GetMethodProperty
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

Visual Studio 會呼叫 debug engine 的 (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)，然後再呼叫 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 來取得堆疊框架上目前方法的相關資訊。

這項的 `IDebugExpressionEvaluator::GetMethodProperty` 執行作業會執行下列工作：

1. 呼叫 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)，傳入 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 物件。 符號提供者 (SP) 會傳回 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) ，代表包含指定之位址的方法。

2. 從取得 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) `IDebugContainerField` 。

3. 具現化類別 (`CFieldProperty` 在此範例中呼叫，此) 範例會執行 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面並包含 `IDebugMethodField` 從 SP 傳回的物件。

4. 傳回 `IDebugProperty2` 物件的介面 `CFieldProperty` 。

## <a name="managed-code"></a>Managed 程式碼
此範例示範 `IDebugExpressionEvaluator::GetMethodProperty` 在 managed 程式碼中的實作為。

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

## <a name="unmanaged-code"></a>非受控碼
此範例顯示 `IDebugExpressionEvaluator::GetMethodProperty` 非受控程式碼中的實作為。

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
- [區域變數的範例執行](../../extensibility/debugger/sample-implementation-of-locals.md)
