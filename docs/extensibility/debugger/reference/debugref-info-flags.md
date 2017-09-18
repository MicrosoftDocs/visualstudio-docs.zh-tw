---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "DEBUGREF_INFO_FLAGS 列舉型別"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取偵錯參考物件的相關資訊。  
  
## 語法  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## Members  
 DEBUGREF\_INFO\_NAME  
 初始化\/使用`bstrName`結構中的欄位。  
  
 DEBUGREF\_INFO\_TYPE  
 初始化\/使用`bstrType`結構中的欄位。  
  
 DEBUGREF\_INFO\_VALUE  
 初始化\/使用`bstrValue`結構中的欄位。  
  
 DEBUGREF\_INFO\_ATTRIB  
 初始化\/使用 `dwAttrib`結構中的欄位。  
  
 DEBUGREF\_INFO\_REFTYPE  
 初始化\/使用`dwRefType`結構中的欄位。  
  
 DEBUGREF\_INFO\_REF  
 初始化\/使用`pReference`結構中的欄位。  
  
 DEBUGREF\_INFO\_VALUE\_AUTOEXPAND  
 \[值\] 欄位應該包含自動展開值，如果可用的話，這種類型的物件。  
  
 DEBUGREF\_INFO\_NONE  
 表示已設定任何旗標。  
  
 DEBUGREF\_INFO\_ALL  
 指示旗標的遮罩。  
  
## 備註  
 這些旗標會傳遞至[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)和[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)方法會指出哪一個欄位的[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構會進行初始化。  
  
 用於`dwFields`成員的`DEBUG_REFERENCE_INFO` ，表示哪些欄位已使用和有效時便會傳回結構的結構。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)