---
title: "取得本機值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "運算式評估、 本機值"
  - "偵錯的 [偵錯 SDK]，本機值"
  - "運算式評估、 入門區域值"
ms.assetid: a10b0764-65ac-476f-bf42-b4a9c38e20de
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 取得本機值
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱 [CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 若要取得的值是在本機，Visual Studio 會呼叫 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 該本機。 在此實作中，類別 `CFieldProperty` IDebugProperty2 介面實作的每個本機。  
  
 這項實作的 `IDebugProperty2::GetPropertyInfo` 會執行下列工作︰  
  
1.  取得區域的名稱、 屬性和屬性從 [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) 結構已具現化這個類別，並將其初始化時填入。  
  
2.  取得區域的類型從 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件。  
  
3.  取得區域的值從 `IDebugField` 物件。 這個欄位繫結至本機使用的記憶體位置 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 物件和值取自產生 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件。  
  
4.  傳回所有要求的內容中 [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) 結構。  
  
## Managed 程式碼  
 這個範例會示範實作 `IDebugProperty2::GetPropertyInfo` 方法的 managed 程式碼在本機。 它也會示範 helper 函式， `Field.GetType`, ，也就是用來取得欄位的類型。`Field.GetValue` 顯示 [評估 \[區域變數\]](../../extensibility/debugger/evaluating-locals.md)。 Helper 函式 `Field.MapModifiersToAttributes` （未顯示） 只是將欄位的轉換 [FIELD\_MODIFIERS](../../extensibility/debugger/reference/field-modifiers.md) 旗標，用於 [DBG\_ATTRIB\_FLAGS](../../extensibility/debugger/reference/dbg-attrib-flags.md) 值。  
  
```c#  
namespace EEMC  
{  
    public class CFieldProperty : IDebugProperty2  
    {  
        public HRESULT GetPropertyInfo(  
            uint                  dwFields,  
            uint                  radix,  
            uint                  timeout,  
            IDebugReference2[]    refArgs,  
            uint                  argCount,   
            DEBUG_PROPERTY_INFO[] infoArray)  
        {  
            DEBUGPROP_INFO_FLAGS flags = (DEBUGPROP_INFO_FLAGS) dwFields;  
            DEBUGPROP_INFO_FLAGS infoFields = DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_NONE;  
  
            // Initialize the structure.  
            DEBUG_PROPERTY_INFO info = infoArray[0];  
            info.pProperty = null;  
  
            // Fill in the full name, if requested.   
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_FULLNAME))  
            {  
                info.bstrFullName = fieldInfo.bstrFullName;  
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_FULLNAME;   
            }  
            // Fill in the name, if requested.   
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_NAME))  
            {  
                info.bstrName = fieldInfo.bstrName;  
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_NAME;   
            }  
            // Fill in the type, if requested.  
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_TYPE))  
            {  
                if (fieldType == null)  
                    fieldType = Field.GetType(field, out fieldSize);  
                if (fieldType == null)  
                    info.bstrType = "unknown";  
                else  
                    info.bstrType = fieldType.ToString();  
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_TYPE;  
            }  
            // The property associated with this property is this property.  
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_PROP))  
            {  
                info.pProperty = this;  
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_PROP;   
            }  
            // Get the property value, if requested.  
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE))  
            {  
                if (fieldType == null)  
                    fieldType = Field.GetType(field, out fieldSize);  
                if (fieldType == null)  
                    info.bstrValue = "?";  
                else  
                {  
                    object o = Field.GetValue(binder, field, fieldType, fieldSize);  
                    if (o == null)  
                        info.bstrValue = "?";  
                    else  
                        info.bstrValue = o.ToString();  
                }  
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE;   
            }  
            // Get the property attributes, if requested.  
            if (0 != (flags & DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_ATTRIB))  
            {  
                info.dwAttrib =   
                    (ulong) Field.MapModifiersToAttributes(  
                        (FIELD_MODIFIERS) fieldInfo.dwModifiers,  
                        fieldKind);  
                infoFields |= DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_ATTRIB;   
            }  
            info.dwFields = (uint) infoFields;  
            infoArray[0] = info;  
            return COM.S_OK;  
        }  
    }  
  
//----------------------------------------------------------------------------  
  
    internal class Field  
    {  
        internal static Type GetType(IDebugField field, out uint size)  
        {  
            size = 0;  
  
            IDebugField fieldType = null;  
            field.GetType(out fieldType);  
            if (fieldType == null)  return null;  
  
            // Get field size.  
            fieldType.GetSize(out size);  
  
            // Get approximate type name.  
            FIELD_INFO[] fieldTypeInfo = new FIELD_INFO[1];  
            fieldType.GetInfo((uint) FIELD_INFO_FIELDS.FIF_NAME,  
                fieldTypeInfo);  
  
            // Map approximate name to type name.  
            switch (fieldTypeInfo[0].bstrName)  
            {  
                case "whole":  
                switch (size)  
                {  
                    case 1: return typeof(sbyte);  
                    case 2: return typeof(short);  
                    case 4: return typeof(int);  
                    case 8: return typeof(long);  
                }  
                    break;  
                case "uwhole":  
                switch (size)  
                {  
                    case 1: return typeof(byte);  
                    case 2: return typeof(char);  
                    case 4: return typeof(uint);  
                    case 8: return typeof(ulong);  
                }  
                    break;  
                case "real":  
                switch (size)  
                {  
                    case 4: return typeof(float);  
                    case 8: return typeof(double);  
                }  
                    break;  
                case "bool": return typeof(bool);  
                case "string": return typeof(string);  
            }  
            return null;  
        }  
}  
```  
  
## Unmanaged 程式碼  
 這個範例會示範實作 `IDebugProperty2::GetPropertyInfo` 方法的本機 unmanaged 程式碼中。 它也會顯示兩個 helper 函式， `FieldGetType` 和 `FieldGetValue` ，用來取得欄位的型別和值，分別。 請注意， `VARIANT`s 用於該欄位的值，做為輸入 `VARIANT` 可以處理各種不同的實值型別。 在此實作中， `FieldGetValue` 傳回 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 晚的物件轉換成值呼叫 `FieldGetPrimitiveValue` \(所示 [評估 \[區域變數\]](../../extensibility/debugger/evaluating-locals.md)\)。  
  
```cpp#  
STDMETHODIMP CFieldProperty::GetPropertyInfo(   
    in  DEBUGPROP_INFO_FLAGS infoFlags,  
    in  DWORD                radix,  
    in  DWORD                timeout,  
    in  IDebugReference2**   ppargs,  
    in  DWORD                argCount,  
    out DEBUG_PROPERTY_INFO* ppropertyInfo  
    )  
{  
    if (!ppropertyInfo)  
        return E_INVALIDARG;  
    else  
        memset(ppropertyInfo,0,sizeof(*ppropertyInfo));  
  
    if (infoFlags & DEBUGPROP_INFO_FULLNAME)  
    {  
        ppropertyInfo->dwFields     |= DEBUGPROP_INFO_FULLNAME;  
        ppropertyInfo->bstrFullName  = SysAllocString( m_fieldInfo.bstrFullName );  
    }  
  
    if (infoFlags & DEBUGPROP_INFO_NAME)  
    {  
        ppropertyInfo->dwFields     |= DEBUGPROP_INFO_NAME;  
        ppropertyInfo->bstrName      = SysAllocString( m_fieldInfo.bstrName );  
    }  
  
    if (infoFlags & DEBUGPROP_INFO_TYPE)  
    {  
        ppropertyInfo->dwFields     |= DEBUGPROP_INFO_TYPE;  
  
        VARIANT type;  
        if (SUCCEEDED(FieldGetType( m_field, &type )))  
        {  
            // Convert the variant's type to a string  
            VariantTypeToString( type, &(ppropertyInfo->bstrType) );  
            VariantClear(&type);  
  
        }  
        if (ppropertyInfo->bstrType == NULL)   
            ppropertyInfo->bstrType = SysAllocString( GetString(IDS_MSG_UNKNOWNTYPE) );  
    }  
  
    if (infoFlags & DEBUGPROP_INFO_PROP)  
    {  
        ppropertyInfo->dwFields     |= DEBUGPROP_INFO_PROP;  
        QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(&(ppropertyInfo->pProperty)) );  
    }  
  
    if (infoFlags & DEBUGPROP_INFO_VALUE)  
    {  
        ppropertyInfo->dwFields   |= DEBUGPROP_INFO_VALUE;  
  
        //only show primitive values  
        VARIANT value;  
        if (SUCCEEDED(FieldGetValue(m_field, &value)))  
        {  
            VariantValueToString( radix, m_binder, value,  
                                  &(ppropertyInfo->bstrValue) );  
            VariantClear(&value);  
        }  
  
        if (ppropertyInfo->bstrValue == NULL)   
            ppropertyInfo->bstrValue = SysAllocString( GetString(IDS_MSG_UNKNOWNVALUE) );  
    }  
  
    if (infoFlags & DEBUGPROP_INFO_VALUE_AUTOEXPAND)  
    {  
    // AUTOEXPAND is ignored in this example  
    }  
  
    if (infoFlags & DEBUGPROP_INFO_ATTRIB)  
    {  
        ppropertyInfo->dwFields   |= DEBUGPROP_INFO_ATTRIB;  
  
        FIELD_MODIFIERS   modifiers = m_fieldInfo.dwModifiers;  
        DBG_ATTRIB_FLAGS  attrib    = DBG_ATTRIB_NONE;  
  
        //access      
        if (modifiers & FIELD_MOD_ACCESS_PUBLIC)  
            attrib |= DBG_ATTRIB_ACCESS_PUBLIC;  
        if (modifiers & FIELD_MOD_ACCESS_PRIVATE)  
            attrib |= DBG_ATTRIB_ACCESS_PRIVATE;  
        if (modifiers & FIELD_MOD_ACCESS_PROTECTED)  
            attrib |= DBG_ATTRIB_ACCESS_PROTECTED;  
        if (modifiers & FIELD_MOD_FINAL)  
            attrib |= DBG_ATTRIB_ACCESS_FINAL;  
  
        //constant  
        if (modifiers & FIELD_MOD_CONSTANT)  
            attrib |= DBG_ATTRIB_VALUE_READONLY;  
  
        //storage  
        if (m_fieldKind & FIELD_SYM_GLOBAL)  
            attrib |= DBG_ATTRIB_STORAGE_GLOBAL;  
        if (modifiers & FIELD_MOD_STATIC)  
            attrib |= DBG_ATTRIB_STORAGE_STATIC;  
  
        //type modifier  
        if (modifiers & FIELD_MOD_VIRTUAL)  
            attrib |= DBG_ATTRIB_TYPE_VIRTUAL;  
        if (modifiers & FIELD_MOD_CONSTANT)  
            attrib |= DBG_ATTRIB_TYPE_CONSTANT;  
        if (modifiers & FIELD_MOD_SYNCHRONIZED)  
            attrib |= DBG_ATTRIB_TYPE_SYNCHRONIZED;  
        if (modifiers & FIELD_MOD_VOLATILE)  
            attrib |= DBG_ATTRIB_TYPE_VOLATILE;  
  
        //type  
        if (m_fieldKind & FIELD_TYPE_METHOD)  
            attrib |= DBG_ATTRIB_METHOD;  
        if (m_fieldKind & FIELD_TYPE_PROP)  
            attrib |= DBG_ATTRIB_PROPERTY;  
        if (m_fieldKind & FIELD_TYPE_CLASS)  
            attrib |= DBG_ATTRIB_CLASS;  
        if (m_fieldKind & FIELD_TYPE_INTERFACE)  
            attrib |= DBG_ATTRIB_INTERFACE;  
        if (m_fieldKind & FIELD_TYPE_INNERCLASS)  
            attrib |= DBG_ATTRIB_INNERCLASS;  
        if (m_fieldKind & FIELD_KIND_SYMBOL)  
            attrib |= DBG_ATTRIB_DATA;  
  
        //set the debug attributes  
        ppropertyInfo->dwAttrib = attrib;  
    }  
  
    return S_OK;  
}  
  
//////////////////////////////////////////////////////////////////////  
// Helper functions  
  
struct PrimitiveTypeInfo  
{  
    LPCOLESTR  pszName;  
    UINT       size;  
    VARTYPE    vt;  
};  
  
PrimitiveTypeInfo primitiveTypeTable[] =  
{  
    { OLE("string"),    0,    VT_BSTR },  
    { OLE("whole"),     1,    VT_I1   },  
    { OLE("whole"),     2,    VT_I2   },  
    { OLE("whole"),     4,    VT_I4   },  
    { OLE("whole"),     8,    VT_I8   },  
    { OLE("uwhole"),    1,    VT_UI1  },  
    { OLE("uwhole"),    2,    VT_UI2  },  
    { OLE("uwhole"),    4,    VT_UI4  },  
    { OLE("uwhole"),    8,    VT_UI8  },  
    { OLE("real"),      4,    VT_R4   },  
    { OLE("real"),      8,    VT_R8   },  
    { OLE("bool"),      1,    VT_BOOL },  
    { OLE("bool"),      2,    VT_BOOL },  
    { OLE("bool"),      4,    VT_BOOL },  
  
    { OLE("System.String"),   0,  VT_BSTR },  
    { OLE("System.SByte"),    1,  VT_I1   },  
    { OLE("System.Int16"),    2,  VT_I2   },  
    { OLE("System.Int32"),    4,  VT_I4   },  
    { OLE("System.Int64"),    8,  VT_I8   },  
    { OLE("System.Byte"),     1,  VT_UI1  },  
    { OLE("System.Char"),     1,  VT_UI2  },  
    { OLE("System.UInt16"),   2,  VT_UI2  },  
    { OLE("System.UInt32"),   4,  VT_UI4  },  
    { OLE("System.UInt64"),   8,  VT_UI8  },  
    { OLE("System.Single"),   4,  VT_R4   },  
    { OLE("System.Double"),   8,  VT_R8   },  
    { OLE("System.Boolean"),  1,  VT_BOOL },  
    { OLE("System.Boolean"),  2,  VT_BOOL },  
    { OLE("System.Boolean"),  4,  VT_BOOL },  
  
    { NULL, 0, VT_EMPTY }  
};  
  
HRESULT FieldGetType( in IDebugField* pfield, out VARIANT* pvarType )  
{  
    HRESULT hr;  
  
    if (pfield == NULL)  
        return E_INVALIDARG;  
    if (pvarType == NULL)  
        return E_INVALIDARG;  
    else  
        *pvarType = 0;  
  
    //get type size and name  
    DWORD        fieldTypeSize;  
    FIELD_INFO   fieldTypeInfo;  
    IDebugField* pfieldType = NULL;  
  
    hr = pfield->GetType( &pfieldType );  
    if (FAILED(hr))  
        return hr;   
  
    hr = pfieldType->GetSize( &fieldTypeSize );  
    if (FAILED(hr))  
    {  
        pfieldType->Release();  
        return hr;  
    }  
  
    hr = pfieldType->GetInfo( FIF_NAME, &fieldTypeInfo );    
    if (FAILED(hr))  
    {  
        pfieldType->Release();  
        return hr;  
    }  
  
    //check for primitive types  
    memset( pvarType, 0, sizeof(*pvarType) );  
    VariantInit(pvarType);  
  
    for (PrimitiveTypeInfo* pprimTypeInfo = primitiveTypeTable;  
         pprimTypeInfo->pszName != NULL;  
         pprimTypeInfo++)  
    {  
        if (pprimTypeInfo->size == fieldTypeSize &&   
           (wcscmp(pprimTypeInfo->pszName,fieldTypeInfo.bstrName) == 0))  
        {  
            pvarType->vt = pprimTypeInfo->vt;  
            break;  
        }  
    }  
  
    //VT_UNKNOWN is used for all other (structured) types  
    if (pvarType->vt == VT_EMPTY)  
    {  
        pvarType->vt      = VT_UNKNOWN;  
        pvarType->punkVal = pfieldType;  
        pvarType->punkVal->AddRef();  
    }  
  
    if (fieldTypeInfo.bstrName != NULL)  
        SysFreeString(fieldTypeInfo.bstrName);  
    pfieldType->Release();  
    return S_OK;  
}  
  
//----------------------------------------------------------------------------  
  
HRESULT FieldGetValue( in IDebugField* pfield, out VARIANT* pvarValue )  
{  
    if (pvarValue == NULL)  
        return E_INVALIDARG;  
    else  
        *pvarValue = 0;  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    //we delay getting the primitive value by just setting VT_UNKNOWN  
    pvarValue->vt      = VT_UNKNOWN;  
    pvarValue->punkVal = pfield;  
    pvarValue->punkVal->AddRef();  
  
    return S_OK;  
}  
```  
  
## 請參閱  
 [範例實作的區域變數](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [取得本機屬性](../../extensibility/debugger/getting-local-properties.md)   
 [評估內容](../../extensibility/debugger/evaluation-context.md)