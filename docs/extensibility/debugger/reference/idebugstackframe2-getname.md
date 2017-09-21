---
title: "IDebugStackFrame2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetName"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetName"
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得堆疊框架的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName (   
   out string pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[\] out傳回的堆疊框架的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 堆疊框架的名稱通常是方法的正在執行名稱。  
  
## 請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)