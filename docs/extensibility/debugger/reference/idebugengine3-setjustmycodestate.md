---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
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
ms.openlocfilehash: 15559f89279ece438ca3af55c1a9936c0b5c4c06
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
This method tells the debug engine about the JustMyCode state information.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `fUpdate`  
 [in] Nonzero (`TRUE`) to update current information, zero (`FALSE`) to reset all information (ignoring anything previously set).  
  
 `dwModules`  
 [in] Number of information structures in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Array of [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) structures to use.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns error code.  
  
## <a name="remarks"></a>Remarks  
 JustMyCode is the concept of debugging only the code that belongs to a user and ignoring all intermediate code such as system code—even if source code is available for that system code.  
  
## <a name="see-also"></a>See Also  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
