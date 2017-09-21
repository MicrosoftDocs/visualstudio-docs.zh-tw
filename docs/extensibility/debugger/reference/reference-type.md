---
title: "REFERENCE_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "REFERENCE_TYPE"
helpviewer_keywords: 
  - "REFERENCE_TYPE 列舉型別"
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# REFERENCE_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定參考的型別。  
  
## 語法  
  
```cpp#  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```c#  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## Members  
 REF\_TYPE\_WEAK  
 指定的弱式參考。  無法與結合`REF_TYPE_STRONG`。  
  
 REF\_TYPE\_STRONG  
 指定強式參考。  無法與結合`REF_TYPE_WEAK`。  
  
## 備註  
 用來作為`dwRefType`成員的[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。  
  
 做為參數來傳遞[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)