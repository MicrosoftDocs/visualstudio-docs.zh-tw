---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

要停止在目前的程式碼位置，或繼續執行，就會告知偵錯引擎 \(DE\)。  
  
## 語法  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### 參數  
 `fCanStop`  
 \[in\]非零值 \(`TRUE`\) 如果 DE 應該停止在目前的程式碼位置。 否則，零 \(`FALSE`\)。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 此事件接收器通常會呼叫[GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)方法，以判定錯誤發生的原因，是想要停止，然後呼叫`IDebugCanStopEvent2::CanStop`與適當回應的方法。  
  
 如果 DE 停止時，它會傳送事件描述停止的原因。  通常有兩個傳送時，使用者或訊號分所代表的事件[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)介面，以及所表示的中斷點事件[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面。  
  
## 請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)