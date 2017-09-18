---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "PROCESS_INFO_FIELDS 列舉型別"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定哪一種處理程序為所擷取的資訊。  
  
## 語法  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## Members  
 PIF\_FILE\_NAME  
 初始化\/使用`bstrFileName`欄位的[PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)結構。  
  
 PIF\_BASE\_NAME  
 初始化\/使用`bstrBaseName`欄位的`PROCESS_INFO`結構。  
  
 PIF\_TITLE  
 初始化\/使用`bstrTitle`欄位的`PROCESS_INFO`結構。  
  
 PIF\_PROCESS\_ID  
 初始化\/使用`ProcessId`欄位的`PROCESS_INFO`結構。  
  
 PIF\_SESSION\_ID  
 初始化\/使用`dwSessionId`欄位的`PROCESS_INFO`結構。  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 初始化\/使用`bstrAttachedSessionName`欄位的`PROCESS_INFO`結構。  
  
 PIF\_CREATION\_TIME  
 初始化\/使用`CreationTime`欄位的`PROCESS_INFO`結構。  
  
 PIF\_FLAGS  
 初始化\/使用`Flags`欄位的`PROCESS_INFO`結構。  
  
 PIF\_ALL  
 請填寫所有欄位。  
  
## 備註  
 傳遞至[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)方法，以指出哪一個欄位的[PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)結構會進行初始化。  
  
 也可用在`Fields`欄位的`PROCESS_INFO` ，表示哪些欄位已使用和有效的結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)