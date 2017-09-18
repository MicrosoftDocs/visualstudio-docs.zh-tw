---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "MODULE_INFO_FIELDS 列舉型別"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定偵錯模組資訊的旗標。  
  
## 語法  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## Members  
 MIF\_NONE  
 初始化\/使用無結構中的欄位。  
  
 MIF\_NAME  
 初始化\/使用`m_bstrName`個[MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)結構。  
  
 MIF\_URL  
 初始化\/使用`m_bstrUrl`個`MODULE_INFO`結構。  
  
 MIF\_VERSION  
 初始化\/使用`m_bstrVersion`個`MODULE_INFO`結構。  
  
 MIF\_DEBUGMESSAGE  
 初始化\/使用`m_bstrDebugMessage`個`MODULE_INFO`結構。  
  
 MIF\_LOADADDRESS  
 初始化\/使用`m_addrLoadAddress`個`MODULE_INFO`結構。  
  
 MIF\_PREFFEREDADDRESS  
 初始化\/使用`m_addrPreferredLoadAddress`個`MODULE_INFO`結構。  
  
 MIF\_SIZE  
 初始化\/使用`m_dwSize`個`MODULE_INFO`結構。  
  
 MIF\_LOADORDER  
 初始化\/使用`m_dwLoadOrder`個`MODULE_INFO`結構。  
  
 MIF\_TIMESTAMP  
 初始化\/使用`m_TimeStamp`個`MODULE_INFO`結構。  
  
 MIF\_URLSYMBOLLOCATION  
 初始化\/使用`m_bstrUrlSymbolLocation`個`MODULE_INFO`結構。  
  
 MIF\_FLAGS  
 初始化\/使用`m_dwModuleFlags`個`MODULE_INFO`結構。  
  
 MIF\_ALLFIELDS  
 初始化\/使用所有的欄位，在`MODULE_INFO`結構。  
  
## 備註  
 這些值會當做引數傳遞[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)方法，以指出哪一個欄位的[MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)結構會進行初始化。  
  
 這些值也可用在`MODULE_INFO` ，表示哪些欄位已使用和有效的結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)