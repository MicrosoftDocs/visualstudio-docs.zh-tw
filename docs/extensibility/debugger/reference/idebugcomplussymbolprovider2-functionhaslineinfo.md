---
title: IDebugComPlus符號提供程式2::功能哈斯林資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FunctionHasLineInfo
- IDebugComPlusSymbolProvider2::FunctionHasLineInfo
ms.assetid: e1b508f1-6521-492f-b110-ab957744a037
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a574766b884bf1aeed253754534fee66967e9ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733454"
---
# <a name="idebugcomplussymbolprovider2functionhaslineinfo"></a>IDebugComPlusSymbolProvider2::FunctionHasLineInfo
確定指定方法是否具有行資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT FunctionHasLineInfo(
    IDebugAddress* pAddress
);
```

```csharp
int FunctionHasLineInfo(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>參數
`pAddress`\
[在]由[IDebugAddress 介面](../../../extensibility/debugger/reference/idebugaddress.md)表示的調試位址。 此地址必須是METHOD_ADDRESS。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,傳`S_FALSE`回 。

## <a name="example"></a>範例
下面的範例展示如何為公開[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)介面的**CDebugSymbol提供程式**物件實現此方法。

```cpp
HRESULT CDebugSymbolProvider::FunctionHasLineInfo(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pAddress, E_INVALIDARG );

    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->FunctionHasLineInfo( address.addr.addr.addrMethod.tokMethod,
                                       address.addr.addr.addrMethod.dwVersion))
    {

        // S_FALSE indicates this method does not have line info

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
