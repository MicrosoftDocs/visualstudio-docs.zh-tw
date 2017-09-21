---
title: "FIELD_KIND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FIELD_KIND_EX 列舉型別"
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列舉其他型態的欄位， [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件可包含。  這個列舉型別擴充[FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md)列舉型別。  
  
## 語法  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```c#  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## Members  
 FIELD\_KIND\_EX\_NONE  
 欄位未包含擴充的型別。  
  
 FIELD\_TYPE\_EX\_METHODVAR  
 欄位會包含方法的變數。  
  
 FIELD\_TYPE\_EX\_CLASSVAR  
 欄位所包含的類別變數。  
  
## 需求  
 標頭: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)