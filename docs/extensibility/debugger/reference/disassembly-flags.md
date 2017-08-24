---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 696900a7080207a4c25280b8cb91fe520331c3a2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Specifies the flags for disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
```cs  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Members  
 DF_DOCUMENTCHANGE  
 Indicates that this instruction is in a different document than the previous one.  
  
 DF_DISABLED  
 Indicates that this instruction will not be executed.  
  
 DF_INSTRUCTION_ACTIVE  
 Indicates that this instruction is one of the next instructions to be executed (there may be more than one).  
  
 DF_DATA  
 Indicates that this instruction is really data (not code).  
  
 DF_HASSOURCE  
 Indicates that this instruction has source. Some instructions, such as profiling or garbage collection code, have no corresponding source.  
  
 DF_DOCUMENT_CHECKSUM  
 Indicates that `bstrDocumentUrl` field contains checksum data after the document URL. See the Remarks section for the [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure for how the checksum data is stored.  
  
## <a name="remarks"></a>Remarks  
 Used as the `dwFlags` member of the [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structure.  
  
 These flags may be combined with a bitwise `OR`.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
