---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
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
ms.openlocfilehash: 259b7137650c1bc9d17e74a07e79543b884312ac
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Terminates the program.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 If possible, the program will be terminated and unloaded from the process; otherwise, the debug engine (DE) will perform any necessary cleanup.  
  
 This method or the [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) method is called by the IDE, typically in response to the user halting all debugging. The implementation of this method should, ideally, terminate the program within the process. If this is not possible, the DE should prevent the program from running any more in this process (and do any necessary cleanup). If the `IDebugProcess2::Terminate` method was called by the IDE, the entire process will be terminated sometime after the `IDebugProgram2::Terminate` method is called.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
