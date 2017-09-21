---
title: "GETNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "GETNAME_TYPE 列舉型別"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取檔案名稱的類型。  
  
## 語法  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## Members  
 GN\_NAME  
 指定文件或內容的好記的名稱。  
  
 GN\_FILENAME  
 指定的文件或內容的完整路徑。  
  
 GN\_BASENAME  
 指定的基底檔名而非文件或內容的完整路徑。  
  
 GN\_MONIKERNAME  
 請指定唯一的名稱的文件或內容 moniker 的形式。  
  
 GN\_URL  
 指定的文件或內容的 URL 名稱。  
  
 GN\_TITLE  
 如果有的話，請指定文件的標題。  
  
 GN\_STARTPAGEURL  
 取得處理序的起始網頁的 URL。  
  
## 備註  
 這些值會做為參數傳遞[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)， [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)，以及[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)來指定何種 name 屬性傳回的方法。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)