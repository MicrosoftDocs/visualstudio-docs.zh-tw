---
title: "dwTYPE_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "dwTYPE_KIND 列舉型別"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定如何解譯的型別[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。  
  
## 語法  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### 參數  
 TYPE\_KIND\_METADATA  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)等位應該解譯成[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)結構。  
  
 TYPE\_KIND\_PDB  
 `TYPE_INFO`等位應該解譯成[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)結構。  
  
 TYPE\_KIND\_BUILT  
 `TYPE_INFO`等位應該解譯成[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)結構。  
  
## 備註  
 這個列舉型別的值會出現在`dwKind`欄位的[TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)架構，用來決定如何解譯`type`等位成員。  `TYPE_INFO`結構就會傳回由呼叫[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)方法。  
  
## 需求  
 標頭: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)