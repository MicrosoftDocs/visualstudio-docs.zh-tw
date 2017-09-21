---
title: "IDebugSymbolProvider::GetLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetLanguage"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetLanguage 方法"
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得用來編譯偵錯的地址的程式碼的語言。  
  
## 語法  
  
```cpp#  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```c#  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### 參數  
 `pAddress`  
 \[in\]地址物件用來表示[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
 `pguidLanguage`  
 \[\] out傳回`GUID`所指定的語言。  
  
 `pguidLanguageVendor`  
 \[\] out傳回`GUID` ，指定的語言廠商。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 偵錯引擎會呼叫這個方法，以取得所選取正確的運算式評估工具所需的資訊。  
  
## 請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)