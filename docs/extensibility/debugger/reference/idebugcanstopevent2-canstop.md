---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: cbf5851c53bc11724b253d8ebc107434bdc9d1f9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifies the debug engine (DE) whether or not to stop at the current code location or just continue execution.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```cs  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `fCanStop`  
 [in] Non-zero (`TRUE`) if the DE should stop at the current code location; otherwise, zero (`FALSE`).  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The receiver of this event typically calls the [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) method to determine the reason the DE wants to stop, and then calls the `IDebugCanStopEvent2::CanStop` method with the appropriate response.  
  
 If the DE stops, it sends an event that describes the reason for stopping. There are typically two events that are sent, a user or signal break represented by the [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interface, and a breakpoint event represented by the [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface.  
  
## <a name="see-also"></a>See Also  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
