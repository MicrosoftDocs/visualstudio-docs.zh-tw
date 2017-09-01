---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e1efd63a837ae86d26b4eebd4851bbfa8d89c4a7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Specifies what information to retrieve about a debug reference object.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Members  
 DEBUGREF_INFO_NAME  
 Initialize/use the `bstrName` field in the structure.  
  
 DEBUGREF_INFO_TYPE  
 Initialize/use the `bstrType` field in the structure.  
  
 DEBUGREF_INFO_VALUE  
 Initialize/use the `bstrValue` field in the structure.  
  
 DEBUGREF_INFO_ATTRIB  
 Initialize/use the `dwAttrib` field in the structure.  
  
 DEBUGREF_INFO_REFTYPE  
 Initialize/use the `dwRefType` field in the structure.  
  
 DEBUGREF_INFO_REF  
 Initialize/use the `pReference` field in the structure.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 The value field should contain the auto-expanded value, if available, for this type of object.  
  
 DEBUGREF_INFO_NONE  
 Indicates that no flags are set.  
  
 DEBUGREF_INFO_ALL  
 Indicates a mask of the flags.  
  
## <a name="remarks"></a>Remarks  
 These flags are passed to the [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) and [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) methods to indicate which fields of the [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) structure are to be initialized.  
  
 Used for the `dwFields` member of the `DEBUG_REFERENCE_INFO` structure to indicate which fields are used and valid when the structure is returned.  
  
 These values may be combined with a bitwise `OR`.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
