---
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
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
ms.openlocfilehash: b97eda0bbd657af67563f4c72566462f55eb5774
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Sets the current instruction pointer to the given code context.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pStackFrame`  
 Reserved for future use; set to a null value.  
  
 `pCodeContext`  
 [in] An [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) object that describes the code location about to be executed and its context.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code. The following table shows other possible values.  
  
|Value|Description|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|The next statement cannot be in a stack frame deeper on the frame stack.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|The next statement is not associated with any frame in the stack.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Some debug engines cannot set the next statement after an exception.|  
  
## <a name="remarks"></a>Remarks  
 The instruction pointer indicates the next instruction or statement to execute. This method is used to retry a line of source code or to force execution to continue in another function, for example.  
  
## <a name="see-also"></a>See Also  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
