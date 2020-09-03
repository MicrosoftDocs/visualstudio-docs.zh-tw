---
title: IDebugComPlusSymbolProvider：： ReplaceSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ReplaceSymbols
- IDebugComPlusSymbolProvider::ReplaceSymbols
ms.assetid: 82fbc8db-c4b1-432f-bec9-1a9dc09570be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90ef0ae096618b776182b397d196f2a4477abe5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733597"
---
# <a name="idebugcomplussymbolproviderreplacesymbols"></a>IDebugComPlusSymbolProvider::ReplaceSymbols
將目前的 debug 符號取代為指定之資料流程中的符號。

## <a name="syntax"></a>語法

```cpp
HRESULT ReplaceSymbols(
    ULONG32  ulAppDomainID,
    GUID     guidModule,
    IStream* pStream
);
```

```csharp
int ReplaceSymbols(
    uint    ulAppDomainID,
    Guid    guidModule,
    IStream pStream
);
```

## <a name="parameters"></a>參數
`ulAppDomainID`\
在應用程式域的識別碼。

`guidModule`\
在模組的唯一識別碼。

`pStream`\
在包含新符號的資料流程。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何針對公開[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的**CDebugSymbolProvider**物件，執行這個方法。

```cpp
HRESULT CDebugSymbolProvider::ReplaceSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IStream* pStream
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::ReplaceSymbols );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->ReplaceSymbols( pStream ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::ReplaceSymbols, hr );
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
