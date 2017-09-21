---
title: "IDebugPortEx2::GetProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::GetProgram"
helpviewer_keywords: 
  - "IDebugPortEx2::GetProgram"
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::GetProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得程式節點相關聯的程式。  
  
## 語法  
  
```cpp#  
HRESULT GetProgram(   
   IDebugProgramNode2* pProgramNode,  
   IDebugProgram2**    ppProgram  
);  
```  
  
```c#  
int GetProgram(   
   IDebugProgramNode2 pProgramNode,  
   out IDebugProgram2 ppProgram  
);  
```  
  
#### 參數  
 `pProgramNode`  
 \[in\][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示 \[程式\] 節點。  
  
 `ppProgram`  
 \[\] out傳回[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示 \[程式\] 節點相關聯的程式。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)