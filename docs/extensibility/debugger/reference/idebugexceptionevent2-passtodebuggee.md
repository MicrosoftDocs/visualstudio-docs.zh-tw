---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定的例外狀況應該傳遞給正在偵錯程式時則繼續執行，或如果應該捨棄例外狀況。  
  
## 語法  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### 參數  
 `fPass`  
 \[in\]非零值 \(`TRUE`\) 如果例外狀況應該傳遞給正在偵錯程式時則繼續執行，則為零 \(`FALSE`\) 如果應該捨棄例外狀況。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法並不會真的會執行所偵錯程式中的任何程式碼。  呼叫是只設定下一個執行的程式碼的狀態。  比方說，要呼叫的方法[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)方法便會傳回`S_OK`與[EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)。`dwState` field set to `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 IDE 可能會收到[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件，並呼叫[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)方法。  偵錯引擎 \(DE\) 應該有預設的行為，來處理案例的 if `PassToDebuggee`不會呼叫方法。  
  
## 請參閱  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)