---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷偵錯引擎 \(DE\) 支援將此例外狀況傳遞給偵錯時繼續執行程式的選項。  
  
## 語法  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## 傳回值  
 傳回其中一個`S_OK` \(例外狀況可以傳送給程式\) 或`S_FALSE` \(不能傳遞例外狀況\)。  
  
## 備註  
 DE 必須要有預設的動作，以便傳遞給偵錯項目。  IDE 可能會收到[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件，並呼叫[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)而不需呼叫的方法`CanPassToDebuggee`方法。  因此，DE 應該有預設理由需要或不在傳遞例外狀況。  
  
## 請參閱  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)