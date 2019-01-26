---
title: IDebugErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf495335fb6522aadb82337e284d299c0fbb8b3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013791"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
這個介面會指定要向使用者回報的錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面來報告錯誤，以人類看得懂的訊息。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並傳送這個事件物件，以報告錯誤。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|`GetErrorMessage`|做為人類看得懂的字串，會傳回錯誤。|  
  
## <a name="remarks"></a>備註  
 如果偵錯引擎發生錯誤時，它可以使用此介面，向使用者報告的訊息，透過 Visual Studio。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)