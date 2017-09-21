---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

停止執行此程式中的所有執行緒。  
  
## 語法  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當這個程式正在偵錯在 multi\-program 的環境中，會呼叫這個方法。  收到來自其他程式停止事件時，會呼叫這個方法，在這個程式。  這個方法的實作應該是非同步的。 也就是不是所有的執行緒應該要以這個方法會傳回前停止。  這個方法的實作可能會像電話一樣簡單[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)在這個程式的方法。  
  
 沒有偵錯事件傳送至這個方法的回應。  
  
## 請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)