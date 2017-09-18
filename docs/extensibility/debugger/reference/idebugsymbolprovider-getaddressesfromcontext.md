---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext 方法"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會將文件內容對應至偵錯位址的陣列。  
  
## 語法  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### 參數  
 `pDocContext`  
 \[in\]文件內容中。  
  
 `fStatmentOnly`  
 \[in\]如果為 TRUE，會限制為單一陳述式的偵錯地址。  
  
 `ppEnumBegAddresses`  
 \[\] out傳回列舉值，這個陳述式或相關行的開始偵錯地址。  
  
 `ppEnumEndAddresses`  
 \[\] out傳回[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)列舉值，這個陳述式或相關線條的結束偵錯地址。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 文件內容通常表示某個範圍的原始程式行。  這個方法會提供的開始與結束偵錯位址這行程式碼。  有些語言允許橫跨多個線路或包含一個以上的陳述式的陳述式。  這個方法會提供旗標來限制為單一陳述式的偵錯地址。  
  
 它有可能有多個偵錯位址，做為範本的大小寫的單一陳述式。  
  
## 請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)