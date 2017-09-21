---
title: "CANSTOP_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CANSTOP_REASON"
helpviewer_keywords: 
  - "CANSTOP_REASON 列舉型別"
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用來決定，是否程式可以停止執行到達某個特定的位置，在執行之後。  
  
## 語法  
  
```cpp#  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```c#  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## Members  
 CANSTOP\_ENTRYPOINT  
 指定的特定程式的進入點。  
  
 CANSTOP\_STEPIN  
 指定逐步執行函式。  
  
## 備註  
 當做引數傳遞[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)方法，以確認的工作階段偵錯管理員 \(SDM\)，如果可以到達程式的進入點之後，或在逐步執行函式或方法時停止。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)