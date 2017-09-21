---
title: "STEPKIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPKIND"
helpviewer_keywords: 
  - "STEPKIND 列舉型別"
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPKIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定逐步執行的步驟類型。  
  
## 語法  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```c#  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## Members  
 STEP\_INTO  
 逐步執行函式。  
  
 STEP\_OVER  
 不是進入函式。  
  
 STEP\_OUT  
 函式的步驟。  
  
 STEP\_BACKWARDS  
 \[逐步執行回溯函式。  
  
## 備註  
 當做引數傳遞[逐步執行](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [逐步執行](../../../extensibility/debugger/reference/idebugprocess3-step.md)