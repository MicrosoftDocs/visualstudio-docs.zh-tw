---
title: "EVENTATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENTATTRIBUTES"
helpviewer_keywords: 
  - "EVENTATTRIBUTES 列舉型別"
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定事件屬性。  
  
## 語法  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```c#  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## Members  
 EVENT\_ASYNCHRONOUS  
 表示事件是非同步，且需要事件未收到回應。  
  
 EVENT\_SYNCHRONOUS  
 指出事件是同步的 ； 藉由回覆[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)。  
  
 EVENT\_STOPPING  
 表示這是停止事件。  其中一個必須結合`EVENT_ASYNCHRONOUS`或`EVENT_SYNCHRONOUS`。  
  
 EVENT\_ASYNC\_STOP  
 指出非同步停止事件。  目前沒有這類事件。  這個旗標是只是預留位置。  
  
 EVENT\_SYNC\_STOP  
 表示同步停止事件 \(結合`EVENT_SYNCHRONOUS`和`EVENT_STOPPING`\)。  當它傳送停止事件時，這個值可供偵錯引擎 \(DE\)。  回覆時所做的呼叫[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)， [逐步執行](../../../extensibility/debugger/reference/idebugprogram2-step.md)，或[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。  
  
 EVENT\_IMMEDIATE  
 表示會立即並以同步方式傳送至 IDE 的事件。  這個旗標會加上其他旗標，就像`EVENT_ASYNCHRONOUS`， `EVENT_SYNCHRONOUS`，或`EVENT_SYNC_STOP`來指示的事件，回覆有更多的機制 \(如果有的話\) 就稱為事實類型。  
  
 EVENT\_EXPRESSION\_EVALUATION  
 此事件很運算式評估的結果。  
  
## 備註  
 這些值以傳送`dwAttrib`參數的[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)