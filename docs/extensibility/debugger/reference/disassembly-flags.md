---
title: "DISASSEMBLY_FLAGS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_FLAGS
helpviewer_keywords: DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1959b101ed5c2aca4c1d806781952ad4e4e6b1ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
指定反組譯碼的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>成員  
 DF_DOCUMENTCHANGE  
 指出這項指示是比前一個不同的文件中。  
  
 DF_DISABLED  
 表示將不會執行這個指令。  
  
 DF_INSTRUCTION_ACTIVE  
 指出這項指示是其中一個要執行下一個程序 （可能會有多個）。  
  
 DF_DATA  
 指出這項指示是實際資料 （而不是程式碼）。  
  
 DF_HASSOURCE  
 指出這個指示有來源。 某些指示，例如程式碼剖析或記憶體回收集合程式碼，有沒有對應的來源。  
  
 DF_DOCUMENT_CHECKSUM  
 表示`bstrDocumentUrl`欄位包含總和檢查碼資料後的文件 URL。 請參閱 < 備註 > 一節的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構儲存的總和檢查碼資料的方式。  
  
## <a name="remarks"></a>備註  
 做為`dwFlags`隸屬[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構。  
  
 這些旗標可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)