---
title: DISASSEMBLY_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b0e4f793b0dcfe7a8a35bfeb06a3acd53c969d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960985"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
指定反組譯碼的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
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
 表示將不會執行這項指示。  
  
 DF_INSTRUCTION_ACTIVE  
 指出這項指示是其中一個要執行的下一步 的指示 （可能會有多個）。  
  
 DF_DATA  
 指出這項指示是真正的資料 （而不是程式碼）。  
  
 DF_HASSOURCE  
 指出這個指示會有來源。 一些指示，例如程式碼剖析或記憶體回收集合程式碼，有沒有對應的來源。  
  
 DF_DOCUMENT_CHECKSUM  
 表示`bstrDocumentUrl`欄位包含總和檢查碼資料，在文件 URL。 請參閱 < 備註 > 一節[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構總和檢查碼資料的儲存方式。  
  
## <a name="remarks"></a>備註  
 做`dwFlags`隸屬[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構。  
  
 這些旗標可能會結合的位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)