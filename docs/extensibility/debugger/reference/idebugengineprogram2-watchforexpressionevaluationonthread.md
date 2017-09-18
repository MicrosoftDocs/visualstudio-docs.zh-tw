---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread"
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

允許 \(或不允許\) 運算式評估在指定的執行緒上發生，即使該程式已停止。  
  
## 語法  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```c#  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### 參數  
 `pOriginatingProgram`  
 \[in\][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示評估運算式的程式。  
  
 `dwTid`  
 \[in\]指定執行緒的識別項。  
  
 `dwEvalFlags`  
 \[in\]從的旗標組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉型別，指定要如何進行評估。  
  
 `pExprCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)是用來傳送運算式的評估期間所發生的偵錯事件的物件。  
  
 `fWatch`  
 \[in\]如果是非零值 \(`TRUE`\)，讓運算式評估所識別的執行緒上`dwTid`。 否則，零 \(`FALSE`\) 不允許在該執行緒上的運算式評估。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當工作階段偵錯管理員 \(SDM\) 會要求程式中，由`pOriginatingProgram`參數，以評估運算式，它藉由呼叫這個方法會告知所有其他附加的程式。  
  
 在一個程式中的運算式評估可能會造成程式碼受限於函式評估或評估的任何執行中， `IDispatch`屬性。  有鑑於此，這個方法會允許執行並完成雖然可能會停止執行緒，此程式中的運算式評估。  
  
## 請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)