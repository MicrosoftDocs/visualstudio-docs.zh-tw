---
title: "取得本機屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式評估、 入門本機內容"
  - "偵錯的 [偵錯 SDK]，本機屬性"
  - "運算式評估、 本機內容"
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 取得本機屬性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 Visual Studio 呼叫 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 取得 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 物件，可讓您存取中顯示所有區域變數 **區域變數** 視窗。 Visual Studio 接著會呼叫 [下一步](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 取得要顯示的每個本機資訊。 在此範例中，類別 `CEnumPropertyInfo` 實作 `IEnumDebugPropertyInfo2` 介面。  
  
 這項實作的 `IEnumDebugPropertyInfo2::Next` 會執行下列工作︰  
  
1.  清除儲存資訊的所在的陣列。  
  
2.  呼叫 [下一步](../../extensibility/debugger/reference/ienumdebugfields-next.md) 每個本機中，儲存傳回 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 傳回陣列中。[IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) 提供物件時這 `CEnumPropertyInfo` 類別具現化。  
  
## Managed 程式碼  
 這個範例會示範實作 `IEnumDebugPropertyInfo2::EnumChildren` 的 managed 程式碼中方法的區域變數。  
  
```c#  
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
  
## Unmanaged 程式碼  
 這個範例會示範實作 `IEnumDebugPropertyInfo2::EnumChildren` 的 unmanaged 程式碼中方法的區域變數。  
  
```cpp#  
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
  
## 請參閱  
 [範例實作的區域變數](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [列舉的區域變數](../../extensibility/debugger/enumerating-locals.md)