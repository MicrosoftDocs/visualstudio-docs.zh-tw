---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會允許連接埠提供者，用以顯示警告，使用者將附加至不安全的程序之前。  
  
## 語法  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## 傳回值  
 傳回值如下所示：  
  
-   `S_OK`： 平安無事附加至處理序並沒有警告\] 對話方塊會顯示。  
  
-   `S_FALSE`： 附加可能有安全性問題，並顯示警告對話方塊。  
  
-   `FAILURE`： 附加至處理序就會失敗。  
  
## 請參閱  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)