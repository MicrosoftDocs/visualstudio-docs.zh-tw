---
title: IDebugComPlusSymbolProvider：： LoadSymbols |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- LoadSymbols
- IDebugComPlusSymbolProvider::LoadSymbols
ms.assetid: 3499680d-0b9a-4f20-8432-c89a41b29b87
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b581be2e1aa64372e98fca0799be25d9000e17e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187185"
---
# <a name="idebugcomplussymbolproviderloadsymbols"></a>IDebugComPlusSymbolProvider::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

在記憶體中載入指定的 debug 符號。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 在應用程式域的識別碼。  
  
 `guidModule`  
 在Mondule 的唯一識別碼。  
  
 `baseAddress`  
 在基本記憶體位址。  
  
 `pUnkMetadataImport`  
 在包含符號中繼資料的物件。  
  
 `bstrModuleName`  
 在模組的名稱。  
  
 `bstrSymSearchPath`  
 在搜尋符號檔的路徑。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何針對公開[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面的**CDebugSymbolProvider**物件，執行這個方法。  
  
```cpp#  
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
