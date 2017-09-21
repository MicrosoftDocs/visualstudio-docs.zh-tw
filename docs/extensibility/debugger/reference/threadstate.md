---
title: "THREADSTATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADSTATE"
helpviewer_keywords: 
  - "THREADSTATE 列舉"
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# THREADSTATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定執行緒的狀態。  
  
## 語法  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```c#  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## Members  
 THREADSTATE\_RUNNING  
 指示執行緒正在執行中。  
  
 THREADSTATE\_STOPPED  
 指出因為中斷點時停止執行緒。  
  
 THREADSTATE\_FRESH  
 指示執行緒已經建立，但還未執行的程式碼。  
  
 THREADSTATE\_DEAD  
 指示執行緒已無作用。  
  
 THREADSTATE\_FROZEN  
 指出執行緒已凍結 \(可以執行任何執行\)。  
  
## 備註  
 用於`dwThreadState`欄位的[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)