---
title: "IDebugProgram2::GetEngineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgram2::GetEngineInfo"
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得名稱和執行這個程式的偵錯引擎 \(DE\) 的 GUID。  
  
## 語法  
  
```cpp#  
HRESULT GetEngineInfo(   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(   
   out string pbstrEngine,  
   out GUID   pguidEngine  
);  
```  
  
#### 參數  
 `pbstrEngine`  
 \[\] out傳回執行此程式 DE 名稱。  
  
 `pguidEngine`  
 \[\] out傳回執行此程式 DE 的 GUID。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 每個 DE 定義它自己的 GUID 來識別身分。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)