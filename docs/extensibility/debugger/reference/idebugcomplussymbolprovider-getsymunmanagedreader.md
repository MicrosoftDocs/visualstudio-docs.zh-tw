---
title: IDebugComPlusSymbolProvider：： GetSymUnmanagedReader |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymUnmanagedReader
- GetSymUnmanagedReader
ms.assetid: 8f1c1627-217f-4405-8141-7a2eb80310a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4463085b021f2de5f9237817b6d8ffade88612a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936154"
---
# <a name="idebugcomplussymbolprovidergetsymunmanagedreader"></a>IDebugComPlusSymbolProvider::GetSymUnmanagedReader
抓取未受管理的程式碼所使用的符號讀取器。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSymUnmanagedReader(
    ULONG32    ulAppDomainID,
    GUID       guidModule,
    IUnknown** ppSymUnmanagedReader
);
```

```csharp
int GetSymUnmanagedReader(
    uint       ulAppDomainID,
    Guid       guidModule,
    out object ppSymUnmanagedReader
);
```

## <a name="parameters"></a>參數
`ulAppDomainID`\
在應用程式域的識別碼。

`guidModule`\
在模組的唯一識別碼。

`ppSymUnmanagedReader`\
擴展傳回代表符號讀取器的物件。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何針對公開 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的 **CDebugSymbolProvider** 物件，執行這個方法。

```cpp
HRESULT CDebugSymbolProvider::GetSymUnmanagedReader(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IUnknown ** ppSymUnmanagedReader
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::GetSymUnmanagedReader );

    IfFailGo( GetModule( idModule, &pModule ) );
    IfFailGo( pModule->GetSymReader((ISymUnmanagedReader**) ppSymUnmanagedReader) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetSymUnmanagedReader, hr );
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
