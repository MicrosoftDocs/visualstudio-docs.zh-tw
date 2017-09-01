---
title: EVALFLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
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
ms.openlocfilehash: c9b711eb4ac8eea64c797c533528069807a1d18a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="evalflags"></a>EVALFLAGS
Specifies flags that control expression evaluation.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Members  
 EVAL_RETURNVALUE  
 Specifies that the return value, if any, be evaluated.  
  
 EVAL_NOSIDEEFFECTS  
 Specifies that side effects not be allowed.  
  
 EVAL_ALLOWBPS  
 Specifies stopping on breakpoints.  
  
 EVAL_ALLOWERRORREPORT  
 Specifies error reporting to the host to be allowed. Primarily used for expression evaluation in script in Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Forces functions to be evaluated as addresses, instead of invoking the function.  
  
 EVAL_NOFUNCEVAL  
 Prevents function from being evaluated. For example, consider the `int` token in the expression `myExpression(int) + 10`. This function can be correctly evaluated as an address, but not as a value.  
  
 EVAL_NOEVENTS  
 Flag to indicate that events that occur during the expression evaluation should not be sent to the session debug manager (SDM) or to the IDE.  
  
## <a name="remarks"></a>Remarks  
 These flags are passed as an argument to the [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) and [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) methods.  
  
 These flags may be combined with a bitwise OR.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
