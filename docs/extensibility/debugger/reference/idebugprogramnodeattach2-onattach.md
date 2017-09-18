---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將附加至相關聯的程式，或聽從附加處理序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
## 語法  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### 參數  
 `guidProgramId`  
 \[in\]`GUID`要指派給相關聯的程式。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)不應該呼叫方法。  否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法會在附加的過程中，之前[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md) ，會呼叫方法。  `OnAttach`方法可執行附加處理序本身 \(在此情況下，這個方法會傳回`S_FALSE`\) 或延後附加處理序`IDebugEngine2::Attach`方法 \( `OnAttach`方法傳回`S_OK`\)。  在可能情況下， `OnAttach`方法可以設定`GUID`來進行偵錯的程式指定`GUID`。  
  
## 請參閱  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)