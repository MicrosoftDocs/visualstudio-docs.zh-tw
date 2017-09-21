---
title: "IDebugPortEx2::TerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::TerminateProcess"
helpviewer_keywords: 
  - "IDebugPortEx2::TerminateProcess"
ms.assetid: bf8fa94c-6d9d-4e4f-ac08-3b44ba5ace68
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::TerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

結束處理程序。  
  
## 語法  
  
```cpp#  
HRESULT TerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```c#  
int TerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### 參數  
 `pPortProcess`  
 \[in\][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示要終止處理程序。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)