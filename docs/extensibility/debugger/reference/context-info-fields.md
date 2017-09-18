---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "CONTEXT_INFO_FIELDS 列舉型別"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取記憶體內容的相關資訊。  
  
## 語法  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## Members  
 CIF\_MODULEURL  
 初始化\/使用`bstrModuleUrl`欄位的[CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)結構。  
  
 CIF\_FUNCTION  
 初始化\/使用`bstrFunction`欄位的`CONTEXT_INFO`結構。  
  
 CIF\_FUNCTIONOFFSET  
 初始化\/使用`posFunctionOffset`欄位的`CONTEXT_INFO`結構。  
  
 CIF\_ADDRESS  
 初始化\/使用`bstrAddress`欄位的`CONTEXT_INFO`結構。  
  
 CIF\_ADDRESSOFFSET  
 初始化\/使用`bstrAddressOffset`欄位的`CONTEXT_INFO`結構。  
  
 CIF\_ALLFIELDS  
 初始化\/使用所有欄位的`CONTEXT_INFO`結構。  
  
## 備註  
 這些值會傳遞該參數用於[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)方法，以指出哪一個欄位的[CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)結構會進行初始化。  
  
 這些旗標也可以用來指出哪一個欄位的`CONTEXT_INFO`結構使用和有效時，會在傳回的結構。  
  
 這些值可以結合使用位元 OR。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)