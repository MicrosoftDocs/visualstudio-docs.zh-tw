---
title: "IDebugProgram2::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::CauseBreak"
helpviewer_keywords: 
  - "IDebugProgram2::CauseBreak"
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

程式停止執行下一個要求的時間它執行緒嘗試執行其中一項。  
  
## 語法  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)當這個程式接下來會嘗試執行程式碼，呼叫這個方法後，事件就會傳送。  
  
 這個方法是非同步的因為此方法會立即傳回而不一定等待程式停止。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)