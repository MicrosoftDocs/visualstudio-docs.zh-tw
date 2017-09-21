---
title: "IDebugPortEx2::GetPortProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::GetPortProcessId"
helpviewer_keywords: 
  - "IDebugPortEx2::GetPortProcessId"
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::GetPortProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得連接埠的處理序 ID。  
  
## 語法  
  
```cpp#  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```c#  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### 參數  
 `pdwProcessId`  
 \[\] out傳回連接埠的實體的處理序 ID。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 Win32 執行時期中，例如，這個方法通常呼叫 Win32 函式`GetCurrentProcessId`以取得實際的處理序 id。  
  
## 請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)