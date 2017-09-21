---
title: "IDebugEngineCreateEvent2::GetEngine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineCreateEvent2::GetEngine"
helpviewer_keywords: 
  - "IDebugEngineCreateEvent2::GetEngine"
ms.assetid: 187d24ed-9f9a-4418-a0ef-b8a19f54652c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineCreateEvent2::GetEngine
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取的物件，表示新建立的偵錯引擎 \(DE\)。  
  
## 語法  
  
```cpp#  
HRESULT GetEngine(   
   IDebugEngine2** pEngine  
);  
```  
  
```c#  
int GetEngine(   
   out IDebugEngine2 pEngine  
);  
```  
  
#### 參數  
 `pEngine`  
 \[\] out傳回[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)物件，表示新建立的 DE。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)