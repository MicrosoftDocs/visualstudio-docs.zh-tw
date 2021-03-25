---
description: 使用指定的回呼方法載入 debug 符號。
title: IDebugComPlusSymbolProvider2：： LoadSymbolsFromCallback |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- LoadSymbolsFromCallback
- IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
ms.assetid: 905315ba-8e9b-4889-b9da-98e1441950ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eac086594a6474f78bdde8b302e8ec24a64f7925
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094155"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromcallback"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromCallback
使用指定的回呼方法載入 debug 符號。

## <a name="syntax"></a>語法

```cpp
HRESULT LoadSymbolsFromCallback(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    IUnknown* pUnkMetadataImport,
    IUnknown* pUnkCorDebugModule,
    BSTR      bstrModuleName,
    BSTR      bstrSymSearchPath,
    IUnknown* pCallback
);
```

```csharp
int LoadSymbolsFromCallback(
    uint   ulAppDomainID,
    Guid   guidModule,
    object pUnkMetadataImport,
    object pUnkCorDebugModule,
    string bstrModuleName,
    string bstrSymSearchPath,
    object pCallback
);
```

## <a name="parameters"></a>參數
`ulAppDomainID`\
在應用程式域的識別碼。

`guidModule`\
在模組的唯一識別碼。

`pUnkMetadataImport`\
在包含符號中繼資料的物件。

`pUnkCorDebugModule`\
在執行 [ICorDebugModule 介面](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface)的物件。

`bstrModuleName`\
在模組的名稱。

`bstrSymSearchPath`\
在搜尋符號檔的路徑。

`pCallback`\
在代表回呼方法的物件。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何針對公開 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)介面的 **CDebugSymbolProvider** 物件，執行這個方法。

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromCallback(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    IUnknown *pMetadataImport,
    IUnknown * _pCorModule,
    BSTR bstrModule,
    BSTR bstrSearchPath,
    IUnknown *pCallback)
{
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");
    USES_CONVERSION;
    EmitTickCount(W2A(bstrModule));

    CAutoLock Lock(this);

    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<ICorDebugModule> pCorModule;

    CModule* pmodule = NULL;
    CModule* pmoduleNew = NULL;
    bool fAlreadyLoaded = false;
    Module_ID idModule(ulAppDomainID, guidModule);
    bool fSymbolsLoaded = false;
    DWORD dwCurrentState = 0;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pMetadataImport, E_INVALIDARG );
    IfFalseGo( _pCorModule, E_INVALIDARG );

    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**)&pMetadata) );

    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,
                                           (void**)&pCorModule) );

    ASSERT(guidModule != GUID_NULL);

    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;

    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );

    //
    // We are now allowing modules to be created that do not have SymReaders.
    // It is likely there are a number of corner cases being ignored
    // that will require knowledge of the hr result below.
    //
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;
    HRESULT hrLoad = pmoduleNew->Create( idModule,
                                         dwCurrentState,
                                         pMetadata,
                                         pCorModule,
                                         bstrModule,
                                         bstrSearchPath,
                                         pCallback );

    if (hrLoad == S_OK)
    {
        fSymbolsLoaded = true;
    }

    // Remove the old module
    if (fAlreadyLoaded)
    {
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));
        RemoveModule( pmodule );
    }

    IfFailGo( AddModule( pmoduleNew ) );

Error:

    RELEASE (pmodule);
    RELEASE (pmoduleNew);

    if (SUCCEEDED(hr) && !fSymbolsLoaded)
    {
        hr = hrLoad;
    }

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );
    EMIT_TICK_COUNT("Exit");
    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
