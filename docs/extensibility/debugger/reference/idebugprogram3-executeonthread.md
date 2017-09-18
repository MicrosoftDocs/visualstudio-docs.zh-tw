---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

執行偵錯工具程式。  執行緒會回到都會提供執行程式時，使用者檢視哪一個執行緒偵錯工具的資訊。  
  
## 語法  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### 參數  
 `pThread`  
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 有三種不同的方式偵錯工具可以繼續執行後停止：  
  
-   執行: 取消任何先前的步驟中，並執行直到下一個中斷點，以此類推。  
  
-   步驟： 取消任何舊的步驟，並執行直到新的步驟完成為止。  
  
-   繼續: 執行一次，並保持作用中的任何舊的步驟。  
  
 執行緒傳遞至`ExecuteOnThread`決定的步驟來取消時非常有用。  如果您不知道執行的執行緒，執行會取消所有的步驟。  了解執行緒，您只需要取消在使用中的執行緒上的步驟。  
  
## 請參閱  
 [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)