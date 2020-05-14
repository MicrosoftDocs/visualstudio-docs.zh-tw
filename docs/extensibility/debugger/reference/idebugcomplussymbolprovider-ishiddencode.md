---
title: IDebugComPlus符號提供程式:隱藏代碼 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsHiddenCode
ms.assetid: 1352c6ab-7b92-4a16-b2d2-6520b628830e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1ede1cbd8c2a69d45a8c653aa97d0bfb618f821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733674"
---
# <a name="idebugcomplussymbolproviderishiddencode"></a>IDebugComPlusSymbolProvider::IsHiddenCode
確定指定除錯器地址的代碼是否隱藏。

## <a name="syntax"></a>語法

```cpp
HRESULT IsHiddenCode(
    IDebugAddress* pAddress
);
```

```csharp
int IsHiddenCode(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>參數
`pAddress`\
[在]由[IDebugAddress 介面](../../../extensibility/debugger/reference/idebugaddress.md)表示的調試位址。

## <a name="return-value"></a>傳回值
如果代碼處於隱藏狀態,則`S_OK`傳回 。否則,傳`S_FALSE`回 。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugComPlusSymbol提供程式](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的**CDebugSymbol提供程式**物件實現此方法。

```cpp
HRESULT CDebugSymbolProvider::IsHiddenCode(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsHiddenCode );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsHiddenCode( address.addr.addr.addrMethod.tokMethod,
                                address.addr.addr.addrMethod.dwVersion,
                                address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates this sequence point is not hidden

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsHiddenCode, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
