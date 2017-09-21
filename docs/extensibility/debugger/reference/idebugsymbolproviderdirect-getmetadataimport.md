---
title: "IDebugSymbolProviderDirect::GetMetaDataImport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMetaDataImport"
  - "IDebugSymbolProviderDirect::GetMetaDataImport"
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMetaDataImport
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取中繼資料匯入資訊。  
  
## 語法  
  
```cpp#  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```c#  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### 參數  
 `guid`  
 \[in\]模組的唯一識別項。  
  
 `appID`  
 \[in\]應用程式定義域的識別項。  
  
 `ppImport`  
 \[\] out傳回物件，其中包含中繼資料匯入資訊。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)