---
title: "IDebugProcess2::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CauseBreak"
helpviewer_keywords: 
  - "IDebugProcess2::CauseBreak"
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

下一步也就是程式執行的程式碼進行這項工作的要求中止，並傳送[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)事件物件。  
  
## 語法  
  
```cpp#  
HRESULT CauseBreak(   
   void  
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)