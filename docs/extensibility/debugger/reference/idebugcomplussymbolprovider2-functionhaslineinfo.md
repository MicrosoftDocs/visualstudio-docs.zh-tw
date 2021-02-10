---
title: IDebugComPlusSymbolProvider2：： FunctionHasLineInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FunctionHasLineInfo
- IDebugComPlusSymbolProvider2::FunctionHasLineInfo
ms.assetid: e1b508f1-6521-492f-b110-ab957744a037
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6492f0899592074e003f49afb06fd9bf7303ddc7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954978"
---
# <a name="idebugcomplussymbolprovider2functionhaslineinfo"></a>IDebugComPlusSymbolProvider2::FunctionHasLineInfo
判斷指定的方法是否具有行資訊。

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
在 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面所代表的偵錯工具位址。 此位址必須是 METHOD_ADDRESS。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 。

## <a name="example"></a>範例
下列範例示範如何針對公開 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)介面的 **CDebugSymbolProvider** 物件，執行這個方法。

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
