---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
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
ms.openlocfilehash: d7a5362aad3a8044ec484f70e71812e45e6a3a8d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Debug engines do not implement this method.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pStackFrame`  
 [in] An [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) object that represents the stack frame.  
  
 `ppLogicalThread`  
 [out] Returns an `IDebugLogicalThread2` interface that represents the associated logical thread. A debug engine implementation should set this to a null value.  
  
## <a name="return-value"></a>Return Value  
 Debug engine implementations always return `E_NOTIMPL`.  
  
## <a name="see-also"></a>See Also  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
