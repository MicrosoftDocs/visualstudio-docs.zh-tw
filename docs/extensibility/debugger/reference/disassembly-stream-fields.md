---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "DISASSEMBLY_STREAM_FIELDS 列舉型別"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定要擷取有關反組譯碼欄位的資訊。  
  
## 語法  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## Members  
 DSF\_ADDRESS  
 初始化\/使用`bstrAddress`欄位。  
  
 DSF\_ADDRESSOFFSET  
 初始化\/使用`bstrAddressOffset`欄位。  
  
 DSF\_CODEBYTES  
 初始化\/使用`bstrCodeBytes`欄位。  
  
 DSF\_OPCODE  
 初始化\/使用`bstrOpCode`欄位。  
  
 DSF\_OPERANDS  
 初始化\/使用`bstrOperands`欄位。  
  
 DSF\_SYMBOL  
 初始化\/使用`bstrSymbol`欄位。  
  
 DSF\_CODELOCATIONID  
 初始化\/使用`uCodeLocationId`欄位。  
  
 DSF\_POSITION  
 初始化\/使用`posBeg`和`posEnd`欄位。  
  
 DSF\_DOCUMENTURL  
 初始化\/使用`bstrDocumentUrl`欄位。  
  
 DSF\_BYTEOFFSET  
 初始化\/使用`dwByteOffset`欄位。  
  
 DSF\_FLAGS  
 初始化\/使用`dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)\) 欄位。  
  
 DSF\_OPERANDS\_SYMBOLS  
 包含在符號名稱`bstrOperands`欄位。  
  
 DSF\_ALL  
 指定反組譯碼資料流的所有欄位。  
  
## 備註  
 做為參數來傳遞[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法，以指出哪一個欄位的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構會進行初始化。  
  
 用於`dwFields`成員的`DisassemblyData` ，表示哪些欄位已使用和有效時便會傳回結構的結構。  
  
 這些值可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)