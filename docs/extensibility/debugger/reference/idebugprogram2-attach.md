---
title: "IDebugProgram2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將附加至程式。  
  
## 語法  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### 參數  
 `pCallback`  
 \[in\][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)要用於偵錯事件告知的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  下表顯示一些可能的錯誤代碼。  
  
|值|描述|  
|-------|--------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的程式已附加偵錯工具。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|附加程序期間，發生安全性違規。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面的程式無法附加至偵錯工具。|  
  
## 備註  
 偵錯引擎 \(DE\) 永遠不會呼叫這個方法，以附加至程式。  如果是執行中程式的位址空間、 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ，會呼叫方法。  如果是執行中工作階段偵錯管理員 」 \(SDM\) 位址空間， [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md) ，會呼叫方法。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)