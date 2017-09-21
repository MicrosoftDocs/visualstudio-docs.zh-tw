---
title: "IDebugComPlusSymbolProvider::ReplaceSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ReplaceSymbols"
  - "IDebugComPlusSymbolProvider::ReplaceSymbols"
ms.assetid: 82fbc8db-c4b1-432f-bec9-1a9dc09570be
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider::ReplaceSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

目前的偵錯符號以取代所指定的資料流中。  
  
## 語法  
  
```cpp#  
HRESULT ReplaceSymbols(  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   IStream* pStream  
);  
```  
  
```c#  
int ReplaceSymbols(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   IStream pStream  
);  
```  
  
#### 參數  
 `ulAppDomainID`  
 \[in\]應用程式定義域的識別項。  
  
 `guidModule`  
 \[in\]模組的唯一的識別項。  
  
 `pStream`  
 \[in\]包含新的符號的資料流。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CDebugSymbolProvider** 物件，公開 \(expose\) [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)介面。  
  
```cpp#  
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
  
## 請參閱  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)