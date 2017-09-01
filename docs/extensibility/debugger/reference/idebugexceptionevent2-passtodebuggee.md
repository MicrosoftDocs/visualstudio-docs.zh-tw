---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
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
ms.openlocfilehash: 9b7ab19e370570dc736ab7685f1bda75aef13981
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Specifies whether the exception should be passed on to the program being debugged when execution resumes, or if the exception should be discarded.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `fPass`  
 [in] Nonzero (`TRUE`) if the exception should be passed on to the program being debugged when execution resumes, or zero (`FALSE`) if the exception should be discarded.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Calling this method does not actually cause any code to be executed in the program being debugged. The call is merely to set the state for the next code execution. For example, calls to the [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) method may return `S_OK` with the [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` field set to `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 The IDE may receive the [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) event and call the [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) method. The debug engine (DE) should have a default behavior to handle the case if the `PassToDebuggee` method is not called.  
  
## <a name="see-also"></a>See Also  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
