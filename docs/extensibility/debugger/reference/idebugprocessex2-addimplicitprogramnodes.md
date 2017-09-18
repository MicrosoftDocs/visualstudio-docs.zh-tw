---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes 方法"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會加入每個偵錯引擎 \(DE\) 所指定的程式\] 節點。  
  
## 語法  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### 參數  
 `guidLaunchingEngine`  
 \[in\]`GUID`的 DE，是要用來啟動程式 \(且假設為加入自己的程式節點\)。  
  
 `rgguidSpecificEngines`  
 \[in\]陣列的`GUID`s 的 DEs 節點將新增的程式。  
  
 `celtSpecificEngines`  
 \[in\]數字`GUID`s `rgguidSpecificEngines`陣列。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [程式節點](../../../extensibility/debugger/program-nodes.md)應加如中所列的每個 DE `rgguidSpecificEngines`— 不包括啟動引擎 \(在一起`guidLaunchingEngine`\)，它會被假設為加入自己的程式\] 節點，啟動程式。  
  
## 請參閱  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [程式節點](../../../extensibility/debugger/program-nodes.md)