---
title: "BPREQI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "BPREQI_FIELDS 列舉型別"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取中斷點要求的相關資訊。  
  
## 語法  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## Members  
 BPREQI\_BPLOCATION  
 初始化\/使用`bpLocation` \(中斷點位置\)\] 欄位中的[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)或[BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。  
  
 BPREQI\_LANGUAGE  
 初始化\/使用`guidLanguage`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_PROGRAM  
 初始化\/使用`pProgram`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_PROGRAMNAME  
 初始化\/使用`bstrProgramName`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_THREAD  
 初始化\/使用`pThread`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_THREADNAME  
 初始化\/使用`bstrThreadName`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_PASSCOUNT  
 初始化\/使用`bpPassCount`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_CONDITION  
 初始化\/使用`bpCondition` \(中斷點條件\) 欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_FLAGS  
 初始化\/使用`dwFlags`欄位的`BP_REQUEST_INFO`或`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_ALLOLDFIELDS  
 初始化\/使用所有欄位的`BP_REQUEST_INFO`結構。  
  
 BPREQI\_VENDOR  
 初始化\/使用`guidVendor`欄位的`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_CONSTRAINT  
 初始化\/使用`bstrConstraint`欄位的`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_TRACEPOINT  
 初始化\/使用`bstrTracepoint`欄位的`BP_REQUEST_INFO2`結構。  
  
 BPREQI\_ALLFIELDS  
 指定所有的欄位，如`BP_REQUEST_INFO2`結構。  
  
## 備註  
 當做引數傳遞[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)和[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)方法，以指定欄位的[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構是進行初始化。  
  
 這些旗標也可以用來指出哪一個欄位的`BP_REQUEST_INFO`和`BP_REQUEST_INFO2`結構是使用和有效，傳回每個結構時。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)