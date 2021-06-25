---
title: 取得區域屬性 |Microsoft Docs
description: 瞭解 Visual Studio 如何使用 EnumChildren 來取得本機屬性，以及這些適用于 managed 和非受控程式碼的範例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c45933c6340836fac889f1309c14a71feed31791
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900729"
---
# <a name="get-local-properties"></a>取得區域屬性
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

Visual Studio 會呼叫 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 來取得 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 物件，該物件會提供要顯示在 [ **區域變數** ] 視窗中的所有區域變數的存取權。 Visual Studio 接著會呼叫 [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 來取得要針對每個本機顯示的資訊。 在此範例中，類別會實 `CEnumPropertyInfo` 作為 `IEnumDebugPropertyInfo2` 介面。

這項的 `IEnumDebugPropertyInfo2::Next` 執行作業會執行下列工作：

1. 清除要儲存資訊的陣列。

2. 呼叫每個本機的 [下一個](../../extensibility/debugger/reference/ienumdebugfields-next.md) ，並將傳回的 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 儲存在要傳回的陣列中。 當這個類別具現化時，就會提供 [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) 物件 `CEnumPropertyInfo` 。

## <a name="managed-code"></a>Managed 程式碼
此範例示範如何 `IEnumDebugPropertyInfo2::EnumChildren` 在 managed 程式碼中針對方法的區域變數執行。

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>非受控碼
 此範例示範如何 `IEnumDebugPropertyInfo2::EnumChildren` 在非受控碼中針對方法的區域變數執行。

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [區域變數的範例執行](../../extensibility/debugger/sample-implementation-of-locals.md)
- [列舉區域變數](../../extensibility/debugger/enumerating-locals.md)
