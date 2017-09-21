---
title: "IDebugProgramPublisher2::PublishProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::PublishProgramNode"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::PublishProgramNode"
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgramPublisher2::PublishProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

讓程式節點可供使用的偵錯引擎 \(DEs\) 和工作階段偵錯管理員 \(SDM\)。  
  
## 語法  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```c#  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### 參數  
 `pProgramNode`  
 \[in\][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，代表若要使用的 \[程式\] 節點。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法可讓查詢的資訊，然後再選取，並加以啟動偵錯的程式。  
  
 若要移除程式\] 節點，從可用性，呼叫[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)方法。  
  
## 請參閱  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)