---
title: BP_CONDITION | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7913b12a72ac269f543fcaa3ac7a8ca355b969ce
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="bpcondition"></a>BP_CONDITION
Describes the conditions under which a breakpoint fires.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```csharp  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## <a name="members"></a>Members  
 `pThread`  
 The [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) object that represents the active thread for the application that contains the breakpoint.  
  
 `styleCondition`  
 A value from the [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) enumeration describing the style of this breakpoint condition.  
  
 `bstrContext`  
 The location of the breakpoint.  
  
 `bstrCondition`  
 The firing condition of the breakpoint.  
  
 `nRadix`  
 Radix to be used in evaluating any numerical information.  
  
## <a name="remarks"></a>Remarks  
 This structure is a member of the [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) and [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structures.  
  
 This structure is also passed as a parameter to the [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) and [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) methods.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
