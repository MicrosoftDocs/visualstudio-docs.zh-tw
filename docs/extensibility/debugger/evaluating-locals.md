---
title: 評估本地人 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaf140a9ddbc7733da4d05450a024c0f0a713712
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738814"
---
# <a name="evaluate-locals"></a>評估本地人
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

呼叫[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)以取得本地值以及本地名稱和類型。 由於本地值取決於程式的當前狀態,因此必須從記憶體中獲取本地值。 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)物件用於將表示本地的[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件綁定到包含該值的記憶體中的相應位置。 記憶體中的此位置由[IDebugObject 物件](../../extensibility/debugger/reference/idebugobject.md)表示。

檢索本地值的此功能封載在執行以下工作的說明器函數中:

1. 將`IDebugField`物件綁定到記憶體以獲取`IDebugObject`物件。

2. 從記憶體中獲取該值。 此值表示為一系列位元組。

3. 根據本地類型設定值的格式。

4. 返回包含本地值的泛型物件。 在 C#`object`中, 這是一`VARIANT`個 ,在 C++中,這是一個 。

## <a name="managed-code"></a>Managed 程式碼
 這是檢索託管代碼中本地值的函數的實現。

```csharp
namespace EEMC
{
    internal class Field
    {
        internal static object GetValue(
            IDebugBinder binder,
            IDebugField field,
            Type t,
            uint size)
        {
            if (t == null || size == 0)  return null;

            IDebugObject debugObject = null;
            binder.Bind(null, field, out debugObject);

            byte[] buffer = new byte[size];
            for (int i = 0; i < size; i++)  buffer[i] = 0;

            debugObject.GetValue(buffer, size);

            if (t == typeof(sbyte)) return (sbyte) buffer[0];
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);
            if (t == typeof(byte))  return buffer[0];
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);
            return null;
        }
    }
}
```

## <a name="unmanaged-code"></a>非託管代碼
 這是檢索非託管代碼中本地值的函數的實現。 `FieldGetType`顯示在[獲取本地值](../../extensibility/debugger/getting-local-values.md)中。

```cpp
HRESULT FieldGetPrimitiveValue(
    in  IDebugBinder* pbinder,
    in  IDebugField*  pfield,
    out VARIANT*      pvarValue
    )
{
    if (pvarValue == NULL)
        return E_INVALIDARG;
    else
        *pvarValue = 0;

    if (pfield == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    UINT          valueSize = 0;
    BYTE*         pvalueBits = NULL;
    IDebugObject* pobject    = NULL;

    //get the value as bits
    hr = pbinder->Bind( NULL, pfield, &pobject );
    if (FAILED(hr))
        return hr;

    hr = pobject->GetSize( &valueSize );
    if (FAILED(hr))
    {
        pobject->Release();
        return hr;
    }

    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));
    if (!pvalueBits)
    {
        pobject->Release();
        return E_OUTOFMEMORY;
    }

    hr = pobject->GetValue( pvalueBits, valueSize );
    pobject->Release();
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //get the type
    VARIANT     valueType;

    hr = FieldGetType( pfield, &valueType );
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //copy a primitive value
    switch (valueType.vt)
    {
    case VT_BSTR:
        {
            pvarValue->vt = VT_BSTR;
            if (valueSize == 0)
                pvarValue->bstrVal = SysAllocString( OLE("") );
            else
                pvarValue->bstrVal =
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),
                                           valueSize );
        }

    case VT_BOOL:
    case VT_I1:
    case VT_I2:
    case VT_I4:
    case VT_I8:
    case VT_UI1:
    case VT_UI2:
    case VT_UI4:
    case VT_UI8:
    case VT_R4:
    case VT_R8:
        pvarValue->vt = valueType.vt;

        if (valueSize > 8)
            valueSize = 8;
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );
        break;

    case VT_VOID:
    case VT_EMPTY:
        pvarValue->vt = valueType.vt;
        break;

    default:
        //not a primitive type
        VariantClear(&valueType);
        free(pvalueBits);
        return E_FAIL;
    }

    free(pvalueBits);
    VariantClear(&valueType);
    return S_OK;
}
```

## <a name="see-also"></a>另請參閱
- [部份變數的樣本實作](../../extensibility/debugger/sample-implementation-of-locals.md)
- [取得本地端值](../../extensibility/debugger/getting-local-values.md)
- [評估上下文](../../extensibility/debugger/evaluation-context.md)
