---
title: IDebugComPlusSymbolProvider::GetAssemblyName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAssemblyName
- GetAssemblyName
ms.assetid: a08cd609-b9b9-47bd-bf73-cbf851285907
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af32775430efb375cca1afcc78d3a463cc2ae749
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925769"
---
# <a name="idebugcomplussymbolprovidergetassemblyname"></a>IDebugComPlusSymbolProvider::GetAssemblyName
擷取其模組和應用程式定義域的組件名稱。  
  
## <a name="syntax"></a>語法  
  
```  
[C++]  
HRESULT GetAssemblyName(  
   ULONG32 ulAppDomainID,  
   GUID    guidModule,  
   BSTR*   pbstrName  
);  
```  
  
```  
[C#]  
int GetAssemblyName(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   string pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ulAppDomainID`  
 [in]應用程式定義域的識別項。  
  
 `guidModule`  
 [in]模組的唯一識別碼。  
  
 `pbstrName`  
 [out]傳回組件的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CDebugSymbolProvider**公開 （expose） 的物件[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面。  
  
```cpp  
HRESULT CDebugSymbolProvider::GetAssemblyName(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    BSTR* pbstrName  
)  
{  
    HRESULT hr = S_OK;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    CComPtr<IMetaDataImport> pMetadata;  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetMetadataForModule );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    *pbstrName = NULL;  
  
    IfFailGo( GetMetadata( idModule, &pMetadata ) );  
    IfFailGo( GetAssemblyName( pMetadata, 0, pbstrName ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetMetadataForModule, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)