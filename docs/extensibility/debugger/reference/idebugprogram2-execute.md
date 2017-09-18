---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

會繼續執行此程式從停止的狀態。  清除任何先前的執行狀態 \(例如，一個步驟中\) 時，程式即開始執行一次。  
  
> [!NOTE]
>  這個方法已被取代。  請改用 [執行](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 方法。  
  
## 語法  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當使用者開始執行，從停止的狀態，在某些其他程式的執行緒中時，這個程式在呼叫這個方法。  當使用者選取，也會呼叫這個方法**開始** 指令從 **偵錯**在 IDE 中的功能表。  這個方法的實作可能會像電話一樣簡單[繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)在程式中目前的執行緒上的方法。  
  
> [!WARNING]
>  不要傳送停止事件或立即 \(同步\) 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫。 否則偵錯工具可能會停止回應。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)