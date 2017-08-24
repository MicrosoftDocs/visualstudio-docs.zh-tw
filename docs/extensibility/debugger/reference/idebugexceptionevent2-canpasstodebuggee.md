---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 56e06b405f08669c340201f3b3a8a3d93fec244f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determines whether or not the debug engine (DE) supports the option of passing this exception to the program being debugged when execution resumes.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```cs  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Return Value  
 Returns either `S_OK` (the exception can be passed to the program) or `S_FALSE` (the exception cannot be passed on).  
  
## <a name="remarks"></a>Remarks  
 The DE must have a default action for passing to the debuggee. The IDE may receive the [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) event and call the [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) method without calling the `CanPassToDebuggee` method. Therefore, the DE should have a default case for passing the exception on or not.  
  
## <a name="see-also"></a>See Also  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
