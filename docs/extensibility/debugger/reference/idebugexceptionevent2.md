---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ac5c3aceb9519d66c185f78bdde37861467ecdf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983870"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
偵錯引擎 (DE) 會將此介面傳送至工作階段的偵錯管理員 (SDM) 中，目前正在執行的程式中擲回例外狀況時。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 會實作這個介面來進行偵錯的程式中，發生例外狀況的報表。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件物件，以報告例外狀況。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugExceptionEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|取得有關引發此事件的例外狀況的詳細的資訊。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|取得引發這個事件的例外狀況擲回的人們可讀取描述。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|決定偵錯引擎 (DE) 支援將此例外狀況傳遞至正在進行偵錯時繼續執行程式的選項。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|指定例外狀況應該傳遞給正在偵錯程式時繼續執行，或如果例外狀況應予捨棄。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>備註  
 在之前傳送事件，DE 會檢查以查看 是否這個例外狀況事件已指定發生第一個或第二個可能發生的例外狀況的先前呼叫所[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)。 如果已指定為第一個可能發生的例外狀況， `IDebugExceptionEvent2` SDM 來傳送事件。 如果沒有，DE 讓應用程式有機會處理例外狀況。 如果未不提供任何例外狀況處理常式，則與例外狀況已指定為第二個可能發生的例外狀況，如果`IDebugExceptionEvent2`SDM 來傳送事件。 否則，DE 繼續執行程式，而且作業系統或執行階段處理的例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)