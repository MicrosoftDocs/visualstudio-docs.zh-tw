---
title: IDebugComPlusSymbolProvider::LoadSymbols |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- LoadSymbols
- IDebugComPlusSymbolProvider::LoadSymbols
ms.assetid: 3499680d-0b9a-4f20-8432-c89a41b29b87
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cfbf15e53a9de0a1b89a854c3c107d0d9cf5542c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953130"
---
# <a name="idebugcomplussymbolproviderloadsymbols"></a>IDebugComPlusSymbolProvider::LoadSymbols
載入記憶體中指定的偵錯符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadSymbols(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   BSTR      bstrModuleName,  
   BSTR      bstrSymSearchPath  
);  
```  
  
```csharp  
int LoadSymbols(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   ulong  baseAddress,  
   object pUnkMetadataImport,  
   string bstrModuleName,  
   string bstrSymSearchPath  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ulAppDomainID`  
 [in]應用程式定義域的識別項。  
  
 `guidModule`  
 [in]Mondule 的唯一識別碼。  
  
 `baseAddress`  
 [in]基底的記憶體位址。  
  
 `pUnkMetadataImport`  
 [in]包含符號的中繼資料的物件。  
  
 `bstrModuleName`  
 [in]模組的名稱。  
  
 `bstrSymSearchPath`  
 [in]若要搜尋符號檔案的路徑。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法，如**CDebugSymbolProvider**公開 （expose） 的物件[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面。  
  
```cpp  
HRESULT CDebugSymbolProvider::LoadSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* _pMetadata,  
    BSTR bstrModule,  
    BSTR bstrSearchPath)  
{  
    return LoadSymbolsWithCorModule(ulAppDomainID, guidModule, baseOffset, _pMetadata, NULL, bstrModule, bstrSearchPath);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)