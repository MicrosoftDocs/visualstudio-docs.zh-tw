---
title: 取得區域變數的屬性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10d4ae8cdcd6223a6e5b8e6311b0091df33c359b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859421"
---
# <a name="get-local-properties"></a>取得本機內容
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 Visual Studio 呼叫[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)若要取得[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，可讓您存取中顯示的所有區域變數**區域變數**視窗。 Visual Studio 接著會呼叫[下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)以取得要顯示的每個本機資訊。 在此範例中，類別`CEnumPropertyInfo`實作`IEnumDebugPropertyInfo2`介面。  
  
 這個實作`IEnumDebugPropertyInfo2::Next`會執行下列工作：  
  
1.  清除儲存資訊的陣列。  
  
2.  呼叫[下一步](../../extensibility/debugger/reference/ienumdebugfields-next.md)的每個區域中，儲存傳回[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)中要傳回的陣列。 [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md)提供物件時這`CEnumPropertyInfo`類別具現化。  
  
## <a name="managed-code"></a>Managed 程式碼  
 此範例示範如何實作`IEnumDebugPropertyInfo2::EnumChildren`的 managed 程式碼中的方法的區域變數。  
  
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
  
## <a name="unmanaged-code"></a>Unmanaged 程式碼  
 此範例示範如何實作`IEnumDebugPropertyInfo2::EnumChildren`的 unmanaged 程式碼中的方法的區域變數。  
  
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
 [區域變數的範例實作](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [列舉區域變數](../../extensibility/debugger/enumerating-locals.md)