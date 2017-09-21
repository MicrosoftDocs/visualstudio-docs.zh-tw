---
title: "IDebugProgram2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetName"
helpviewer_keywords: 
  - "IDebugProgram2::GetName"
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得程式的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(   
   out string pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[\] out傳回程式的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法所傳回的名稱永遠會是其中含有一個描述程式的使用者可顯示好記名稱。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)