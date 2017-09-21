---
title: "IDebugProcess2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetServer"
helpviewer_keywords: 
  - "IDebugProcess2::GetServer"
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProcess2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得的伺服器上執行此程序。  
  
## 語法  
  
```cpp#  
HRESULT GetServer(   
   IDebugCoreServer2** ppServer  
);  
```  
  
```c#  
int GetServer(   
   out IDebugCoreServer2 ppServer  
);  
```  
  
#### 參數  
 `ppServer`  
 \[\] out傳回[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)物件，代表此程序正在執行的伺服器。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 可以在單一機器上執行一個以上的伺服器。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)