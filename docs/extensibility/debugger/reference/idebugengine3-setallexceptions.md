---
title: "IDebugEngine3::SetAllExceptions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetAllExceptions"
helpviewer_keywords: 
  - "IDebugEngine3::SetAllExceptions"
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine3::SetAllExceptions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會設定所有未處理的例外狀況的狀態。  
  
## 語法  
  
```cpp  
HRESULT SetAllExceptions(  
   EXCEPTION_STATE dwState  
);  
```  
  
```c#  
int SetAllExceptions(  
   enum_EXCEPTION_STATE dwState  
);  
```  
  
#### 參數  
 `dwState`  
 \[in\]其中[EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)的值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)