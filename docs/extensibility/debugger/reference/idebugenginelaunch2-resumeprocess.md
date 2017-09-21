---
title: "IDebugEngineLaunch2::ResumeProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::ResumeProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::ResumeProcess"
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineLaunch2::ResumeProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

便會繼續處理執行。  
  
## 語法  
  
```cpp#  
HRESULT ResumeProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int ResumeProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### 參數  
 `pProcess`  
 \[in\][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示處理程序繼續執行。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 備註  
 已啟動處理程序呼叫之後，會呼叫這個方法[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法。  
  
## 請參閱  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)