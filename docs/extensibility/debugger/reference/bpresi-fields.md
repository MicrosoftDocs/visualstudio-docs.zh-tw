---
title: "BPRESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "BPRESI_FIELDS 列舉型別"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取成功解析中斷點的相關資訊。  
  
## 語法  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## Members  
 BPRESI\_BPRESLOCATION  
 初始化\/使用`bpResLocation` \(中斷點解析度位置\)\] 欄位中的[BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構。  
  
 BPRESI\_PROGRAM  
 初始化\/使用`pProgram`欄位的`BP_RESOLUTION_INFO`結構。  
  
 BPRESI\_THREAD  
 初始化\/使用`pThread`欄位的`BP_RESOLUTION_INFO`結構。  
  
 BPRESI\_ALLFIELDS  
 指定所有的欄位。  
  
## 備註  
 傳遞至[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)方法，以指出哪一個欄位的[BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構會進行初始化。  
  
 這些旗標也可以用來指出哪一個欄位的`BP_RESOLUTION_INFO`結構使用和有效時，會傳回該結構。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)