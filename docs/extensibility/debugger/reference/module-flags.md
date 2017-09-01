---
title: MODULE_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
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
ms.openlocfilehash: 2bb42c4a29330d2f554c2f2f05273349747addf9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="moduleflags"></a>MODULE_FLAGS
Used to describe a module.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Members  
 MODULE_FLAG_NONE  
 Specifies no module.  
  
 MODULE_FLAG_SYSTEM  
 Specifies a system module.  
  
 MODULE_FLAG_SYMBOLS  
 Specifies a symbol module.  
  
 MODULE_FLAG_64BIT  
 Specifies a 64-bit module.  
  
 MODULE_FLAG_OPTIMIZED  
 Specifies the module has been optimized. This state is reflected in the **Modules** window.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Specifies the module has not been optimized. This state is reflected in the **Modules** window. This is the default state.  
  
## <a name="remarks"></a>Remarks  
 Used for the `m_dwModuleFlags` member of the [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) structure.  
  
 These flags may be combined with a bitwise `OR`.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
