---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "THREADPROPERTY_FIELDS 列舉型別"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取執行緒的相關資訊。  
  
## 語法  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Members  
 TPF\_ID  
 初始化\/使用`dwThreadId`欄位的[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。  
  
 TPF\_SUSPENDCOUNT  
 初始化\/使用`dwSuspendCount`欄位的`THREADPROPERTIE`s 的結構。  
  
 TPF\_STATE  
 初始化\/使用`dwThreadState`欄位的`THREADPROPERTIE`s 的結構。  
  
 TPF\_PRIORITY  
 初始化\/使用`bstrPriority`欄位的`THREADPROPERTIE`s 的結構。  
  
 TPF\_NAME  
 初始化\/使用`bstrName`欄位的`THREADPROPERTIE`s 的結構。  
  
 TPF\_LOCATION  
 初始化\/使用`bstrLocation`欄位的`THREADPROPERTIE`s 的結構。  
  
 TPF\_ALLFIELDS  
 指定所有的欄位。  
  
## 備註  
 這些值會當做引數傳遞[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法，以指出哪一個欄位的[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構會進行初始化。  
  
 這些值也可用在`dwFields`成員的`THREADPROPERTIES` ，表示哪些欄位已使用和有效的結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)