---
title: IDebugBinder3::獲取記憶體上下文64 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMemoryContext64
- IDebugBinder3::GetMemoryContext64
ms.assetid: f021fd16-9fc7-4c41-86af-e54e6224cfbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f76d84f0403a853ae7e297084f8745d7428386a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735735"
---
# <a name="idebugbinder3getmemorycontext64"></a>IDebugBinder3::GetMemoryContext64
將物件位置或 64 位元記憶體位址轉換為記憶體上下文。

## <a name="syntax"></a>語法

```cpp
HRESULT GetMemoryContext64 (
    IDebugField*           pField,
    UINT64                 uConstant,
    IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext64 (
    IDebugField              pField,
    ulong                    uConstant,
    out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>參數
`pField`\
[在]描述要定位的物件的[IDebugField。](../../../extensibility/debugger/reference/idebugfield.md) 如果`NULL`,`dwConstant`則改用。

`uConstant`\
[在]64 位記憶體位址,如 0x50000000。

`ppMemCxt`\
[出]返回表示物件位址或記憶體中位址的[IDebugMemoryMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="example"></a>範例
以下範例創建一個實現[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)介面並使用此方法檢索記憶體上下文的物件。

```cpp
HRESULT CValueProperty::GetMemoryContext ( IDebugMemoryContext2** out_ppMemoryContext )
{
    // precondition
    REQUIRE( NULL != out_ppMemoryContext );

    if (NULL == out_ppMemoryContext)
        return E_POINTER;

    *out_ppMemoryContext = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    if (VT_EMPTY == this->m_VarValue.vt)
    {
        return E_FAIL;
    }

    // function body
    if (NULL != this->m_pBinder)
    {
        UINT64 dwOffset = 0;

        DEBUG_PROPERTY_INFO dpInfo;
        HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_VALUE,
                                           10, // RADIX
                                           DEFAULT_TIMEOUT,
                                           NULL,
                                           0,
                                           &dpInfo);
        if (ENSURE( S_OK == HR ))
        {
            REQUIRE( NULL != dpInfo.bstrValue );
            REQUIRE( NULL == dpInfo.bstrName );
            REQUIRE( NULL == dpInfo.bstrFullName );
            REQUIRE( NULL == dpInfo.bstrType );
            REQUIRE( NULL == dpInfo.pProperty );

            wchar_t * end;
            dwOffset = _wcstoui64(dpInfo.bstrValue, &end, 0); // base 0 to allow 0x if it's ever output
            ::SysFreeString(dpInfo.bstrValue);
        }

        if (CComQIPtr<IDebugBinder3> binder3 = this->m_pBinder)
            HR = binder3->GetMemoryContext64(NULL, dwOffset, out_ppMemoryContext);
        else
            HR = this->m_pBinder->GetMemoryContext(NULL, (DWORD)(__int32)dwOffset, out_ppMemoryContext);

        if (ENSURE( S_OK == HR ))
        {
            REQUIRE( NULL != *out_ppMemoryContext );
        }
    }

    // postcondition
    INVARIANT( this );

    HRESULT HR = E_FAIL;

    if (NULL != *out_ppMemoryContext)
    {
        HR = S_OK;
    }

    return HR;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
