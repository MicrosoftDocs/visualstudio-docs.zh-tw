---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "FIELD_INFO_FIELDS 列舉型別"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取有關的資訊[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## 語法  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## Members  
 FIF\_FULLNAME  
 初始化\/使用`bstrFullName`個[FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)結構。  
  
 FIF\_NAME  
 初始化\/使用`bstrName`個`FIELD_INFO`結構。  
  
 FIF\_TYPE  
 初始化\/使用`bstrType`個`FIELD_INFO`結構。  
  
 FIF\_MODIFIERS  
 初始化\/使用`bstrModifiers`個`FIELD_INFO`結構。  
  
## 備註  
 這些值也會傳遞做為引數以[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)方法，以指定那一個欄位的[FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)結構會進行初始化。  
  
 這些值也可用在`dwFields`成員的`FIELD_INFO` ，表示哪些欄位已使用和有效的結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)