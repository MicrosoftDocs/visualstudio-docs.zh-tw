---
title: "IDebugProgramHost2::GetHostName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostName"
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得標題、 好記的名稱或檔名的裝載處理序，此程式。  
  
## 語法  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### 參數  
 `dwType`  
 \[in\]介於[GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列舉型別。  
  
 `pbstrHostName`  
 \[\] out傳回要求的裝載處理序的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 在典型的實作，這個方法中， `dwType`參數會被忽略，並傳回主機上的好記的名稱。  另一個可能的實作是將`dwType`參數來呼叫[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法來取得名稱。  
  
## 請參閱  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)