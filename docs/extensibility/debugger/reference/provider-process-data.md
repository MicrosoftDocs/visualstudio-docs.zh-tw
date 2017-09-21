---
title: "PROVIDER_PROCESS_DATA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_PROCESS_DATA"
helpviewer_keywords: 
  - "PROVIDER_PROCESS_DATA 結構"
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此結構會提供電腦上執行的處理序的資訊。  
  
## 語法  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```c#  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## Members  
 欄位  
 從的旗標組合[PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)列舉型別，指出要填入哪些欄位。  
  
 ProgramNodes  
 A [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)結構，其中包含一系列程式的節點。  
  
 fIsDebuggerPresent  
 非零值 \(`TRUE`\) 如果[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具正在執行中，零 \(`FALSE`\) 如果它不是。  
  
## 備註  
 這個結構會傳遞至[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)填滿其中的方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)