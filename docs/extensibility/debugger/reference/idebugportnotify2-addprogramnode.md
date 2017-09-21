---
title: "IDebugPortNotify2::AddProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2::AddProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::AddProgramNode"
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortNotify2::AddProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

註冊連接埠執行的程式，才能進行偵錯。  
  
## 語法  
  
```cpp#  
HRESULT AddProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int AddProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### 參數  
 `pProgramNode`  
 \[in\][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示要註冊的程式。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 程式節點可以取消登錄從連接埠藉由呼叫[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)方法。  
  
## 請參閱  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)