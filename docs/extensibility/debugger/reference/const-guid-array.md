---
title: "CONST_GUID_ARRAY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONST_GUID_ARRAY"
helpviewer_keywords: 
  - "CONST_GUID_ARRAY 結構"
ms.assetid: bd55e7d8-372c-4c3e-9eed-28f6b415a5db
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# CONST_GUID_ARRAY
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

一種結構，保留一份`GUID`s。  
  
## 語法  
  
```cpp#  
typedef struct tagCONST_GUID_ARRAY {  
   DWORD       dwCount;  
   CONST GUID* Members;  
} CONST_GUID_ARRAY;  
```  
  
```c#  
public struct CONST_GUID_ARRAY {  
   public uint   dwCount;  
   public Guid[] Members;  
}  
```  
  
## Members  
 dwCount  
 數字的`GUID`s `Members`陣列。  
  
 Members  
 陣列的`GUID`s。  
  
## 備註  
 這個結構會傳遞至[PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md)方法，並傳回的[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)和[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)方法。  
  
 這個結構的執行個體的擁有者負責釋放配置任何記憶體。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)   
 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)