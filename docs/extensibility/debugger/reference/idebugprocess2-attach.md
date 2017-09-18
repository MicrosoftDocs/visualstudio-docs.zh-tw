---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將工作階段偵錯管理員 \(SDM\) 附加至處理序。  
  
## 語法  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### 參數  
 `pCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)用於偵錯事件告知的物件。  
  
 `rgguidSpecificEngines`  
 \[in\]Guid 的偵錯引擎，以用於偵錯的處理序中執行的程式陣列。  這個參數可以是 null 值。  如需詳細資訊，請參閱 「 備註 」。  
  
 `celtSpecificEngines`  
 \[in\]偵錯引擎在`rgguidSpecificEngines`陣列和大小的`rghrEngineAttach`陣列。  
  
 `rghrEngineAttach`  
 輸入 \[、 輸出\]偵錯引擎所傳回的 HRESULT 代碼的陣列。  此陣列的大小控制台中`celtSpecificEngines`參數。  每個程式碼通常是其中一個`S_OK`或`S_ATTACH_DEFERRED`。  後者表示目前的程式沒有附加 DE。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示其他可能的值。  
  
|值|描述|  
|-------|--------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的處理序已附加偵錯工具。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|附加程序期間，發生安全性違規。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌上型電腦的處理程序無法附加至偵錯工具。|  
  
## 備註  
 附加至處理序附加至偵錯引擎 \(DE\) 控制台中才能進行偵錯該處理序中執行的所有程式的 SDM `rgguidSpecificEngines`陣列。  設定`rgguidSpecificEngines`設為 null 的參數值，或包含`GUID_NULL`陣列中要附加至處理序中的所有程式。  
  
 在處理程序中發生的所有偵錯事件都傳送到指定[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。  這`IDebugEventCallback2` SDM 會呼叫這個方法時，提供物件。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)