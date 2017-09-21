---
title: "IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule"
  - "LoadSymbolsFromStreamWithCorModule"
ms.assetid: f79b894f-52c4-43c2-9a68-c71536451f6c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

從指定的資料流載入偵錯符號 **ICorDebugModule** 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT LoadSymbolsFromStreamWithCorModule(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   IStream*  pStream  
);  
```  
  
```c#  
int LoadSymbolsFromStreamWithCorModule(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   object  pUnkCorDebugModule,  
   IStream pStream  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ulAppDomainID`  
 [in]應用程式定義域的識別項。  
  
 `guidModule`  
 [in]模組的唯一識別碼。  
  
 `baseAddress`  
 [in]基底的記憶體位址。  
  
 `pUnkMetadataImport`  
 [in]包含符號中繼資料的物件。  
  
 `pUnkCorDebugModule`  
 [in]實作物件 [ICorDebugModule 介面](ICorDebugModule%20Interface.xml)。  
  
 `pStream`  
 [in]包含要載入的偵錯符號的資料流。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法的 **CDebugSymbolProvider** 公開物件 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) 介面。  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStreamWithCorModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IUnknown* pUnkCorDebugModule,  
    IStream* pStream  
)  
{  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pUnkMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbolsFromStream );  
  
    IfFalseGo( pUnkMetadataImport, E_INVALIDARG );  
    IfFalseGo( pUnkCorDebugModule, E_INVALIDARG );  
  
    IfFailGo( pUnkMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( pUnkCorDebugModule->QueryInterface( IID_ICorDebugModule,  
              (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
  
    IfFailGo( pmoduleNew->Create( idModule,  
                                  dwCurrentState,  
                                  pMetadata,  
                                  pCorModule,  
                                  pStream,  
                                  baseOffset ) );  
  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule(pmodule);  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbolsFromStream, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)