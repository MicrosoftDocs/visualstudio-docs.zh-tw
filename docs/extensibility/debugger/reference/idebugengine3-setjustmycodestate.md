---
title: "IDebugEngine3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugEngine3::SetJustMyCodeState"
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會告知偵錯引擎 JustMyCode 狀態資訊。  
  
## 語法  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### 參數  
 `fUpdate`  
 \[in\]非零值 \(`TRUE`\) 來更新目前的資訊，請為零 \(`FALSE`\) 來重設 \(略過任何先前設定\) 的所有資訊。  
  
 `dwModules`  
 \[in\]資訊結構中的數字`rgJMCSpec.`  
  
 `rgJMCSpec`  
 \[in\]陣列的[JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)若要使用的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 JustMyCode 是屬於使用者程式碼偵錯，並忽略所有的中繼程式碼，例如系統的程式碼的概念，即使原始碼適用於該系統程式碼。  
  
## 請參閱  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)