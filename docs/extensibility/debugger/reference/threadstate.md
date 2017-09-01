---
title: THREADSTATE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
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
ms.openlocfilehash: 32e6781b57a60ac39fa932ac5df5aea9e36b07b2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="threadstate"></a>THREADSTATE
Specifies the state of the thread.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Members  
 THREADSTATE_RUNNING  
 Indicates that the thread is running.  
  
 THREADSTATE_STOPPED  
 Indicates that the thread is stopped because of a breakpoint.  
  
 THREADSTATE_FRESH  
 Indicates that the thread has been created, but is not yet running code.  
  
 THREADSTATE_DEAD  
 Indicates that the thread is dead.  
  
 THREADSTATE_FROZEN  
 Indicates that the thread is frozen (no execution can be performed).  
  
## <a name="remarks"></a>Remarks  
 Used for the `dwThreadState` field of the [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) structure.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
