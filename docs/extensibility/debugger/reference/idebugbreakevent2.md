---
title: IDebugBreakEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d23a8c534ba3d829a02075d2d195689df6d08482
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857500"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
這個介面會告知工作階段的偵錯管理員 (SDM) 已成功完成非同步的中斷。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 DE 會實作這個介面來支援在程式中的使用者符號。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上 (使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 SDM 呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)當使用者已要求要暫停進行偵錯的程式。 當已成功暫停程式時，會將傳送 DE`IDebugBreakEvent2`事件。 此事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，在 SDM 所提供的回呼函式。  
  
## <a name="remarks"></a>備註  
 例如，使用者可以選取**全部中斷**命令**偵錯**功能表來中斷程式執行無限迴圈。 在 SDM 會告訴程式停止藉由呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)。 DE 傳送`IDebugBreakEvent2`最後停止程式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)