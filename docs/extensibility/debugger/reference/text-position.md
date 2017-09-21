---
title: "TEXT_POSITION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TEXT_POSITION"
helpviewer_keywords: 
  - "TEXT_POSITION 結構"
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# TEXT_POSITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述在指定的文字行和資料行的位置。  
  
## 語法  
  
```cpp#  
typedef struct _tagTEXT_POSITION {   
   DWORD dwLine;  
   DWORD dwColumn;  
} TEXT_POSITION;  
```  
  
```c#  
public struct TEXT_POSITION {   
   public uint dwLine;  
   public uint dwColumn;  
};  
```  
  
## Members  
 dwLine  
 原始程式檔中的行索引。  
  
 dwColumn  
 到一行的字元位移。  
  
## 備註  
 這個結構用在[CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)和[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構。  
  
 這個結構會填入呼叫下列方法：  
  
-   [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)  
  
-   [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)  
  
-   [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)  
  
-   [GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)  
  
 這個結構當做參數傳遞，以下列方法：  
  
-   [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)  
  
-   [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)  
  
-   [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)  
  
-   [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)  
  
-   [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)   
 [GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)   
 [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)