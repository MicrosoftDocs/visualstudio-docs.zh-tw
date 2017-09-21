---
title: "MODULE_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "MODULE_FLAGS 列舉型別"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用來描述模組。  
  
## 語法  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## Members  
 MODULE\_FLAG\_NONE  
 指定沒有模組。  
  
 MODULE\_FLAG\_SYSTEM  
 指定系統模組。  
  
 MODULE\_FLAG\_SYMBOLS  
 指定符號的模組。  
  
 MODULE\_FLAG\_64BIT  
 指定的 64 位元模組。  
  
 MODULE\_FLAG\_OPTIMIZED  
 指定的模組已經過最佳化。  此狀態會反映在**模組**視窗。  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 指定的模組未最佳化。  此狀態會反映在**模組**視窗。  這是預設狀態。  
  
## 備註  
 用於`m_dwModuleFlags`成員的[MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)