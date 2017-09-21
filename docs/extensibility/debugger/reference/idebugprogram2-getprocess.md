---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

完成該琵序中執行這個程式。  
  
## 語法  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### 參數  
 `ppProcess`  
 \[\] out傳回[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) ，表示處理程序的介面。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 除非偵錯引擎 \(DE\) 實作[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)介面，這個方法是實作應該永遠會傳回`E_NOTIMPL` ，因為將 DE 無法判斷哪個處理程序，它正在執行中，因此也無法滿足此方法的實作。  
  
 實作`IDebugEngineLaunch2`介面表示 DE 必須知道如何建立處理程序。 因此，DE 實作[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面就能夠知道它正在執行中的何種處理程序。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)