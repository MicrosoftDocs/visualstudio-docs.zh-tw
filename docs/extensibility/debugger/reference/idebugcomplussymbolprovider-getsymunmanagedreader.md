---
title: IDebugComPlusSymbolProvider::GetSymUnmanagedReader |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymUnmanagedReader
- GetSymUnmanagedReader
ms.assetid: 8f1c1627-217f-4405-8141-7a2eb80310a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33c2a4add0f09df2aa28074c5c13b3df4ce43567
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109122"
---
# <a name="idebugcomplussymbolprovidergetsymunmanagedreader"></a>IDebugComPlusSymbolProvider::GetSymUnmanagedReader
擷取至 unmanaged 程式碼所使用的符號讀取器。  
  
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
  
#### <a name="parameters"></a>參數  
 `ulAppDomainID`  
 [in]應用程式定義域的識別項。  
  
 `guidModule`  
 [in]模組的唯一識別碼。  
  
 `ppSymUnmanagedReader`  
 [out]傳回表示的符號讀取器的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來**CDebugSymbolProvider**公開物件[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面。  
  
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
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)