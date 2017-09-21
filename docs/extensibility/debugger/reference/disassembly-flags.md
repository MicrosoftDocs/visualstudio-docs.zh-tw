---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "DISASSEMBLY_FLAGS 列舉型別"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定反組譯碼的旗標。  
  
## 語法  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## Members  
 DF\_DOCUMENTCHANGE  
 表示此指令位於比前一個不同的文件。  
  
 DF\_DISABLED  
 表示將不會執行這個指令。  
  
 DF\_INSTRUCTION\_ACTIVE  
 表示這個指令為其中一個要執行下一個程序 \(可能會有一個以上\)。  
  
 DF\_DATA  
 表示這個指令其實資料 \(而不是程式碼\)。  
  
 DF\_HASSOURCE  
 表示此指令有來源。  部份的指示，例如程式碼剖析或廢棄項目集合程式碼，有沒有對應的來源。  
  
 DF\_DOCUMENT\_CHECKSUM  
 表示`bstrDocumentUrl` 」 欄位包含總和檢查碼資料後的文件的 URL。  請參閱 \[備註\] 部份的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構的總和檢查碼資料的儲存方式。  
  
## 備註  
 用來作為`dwFlags`成員的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構。  
  
 這些旗標可以使用位元和結合`OR`。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)