---
title: "IDebugEngine2::DestroyProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::DestroyProgram"
helpviewer_keywords: 
  - "IDebugEngine2::DestroyProgram"
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

告知偵錯引擎 \(DE\) 不規則終止指定的程式，且 DE 應清除該程式的所有參考，並傳送程式損毀的事件。  
  
## 語法  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### 參數  
 `pProgram`  
 \[in\][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示已經終止了不規則的程式。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 在呼叫這個方法之後，接下來會傳送 DE [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)回工作階段偵錯管理員 \(SDM\) 的事件。  
  
 未實作這個方法 \(會傳回`E_NOTIMPL`\) 如果 DE 執行相同的處理序偵錯程式中。  只有當 DE 執行 SDM 相同的處理序中實作這個方法。  
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)