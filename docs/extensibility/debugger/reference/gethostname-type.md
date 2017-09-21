---
title: "GETHOSTNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETHOSTNAME_TYPE"
helpviewer_keywords: 
  - "GETHOSTNAME_TYPE 列舉型別"
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GETHOSTNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定主機名稱的型的別。  
  
## 語法  
  
```cpp#  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```c#  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## Members  
 GHN\_FRIENDLY\_NAME  
 指定主應用程式的好記的名稱。  
  
 GHN\_FILE\_NAME  
 指定的檔名的主應用程式。  
  
## 備註  
 這些值會當做引數傳遞[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法，以擷取不同格式的主機名稱。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)