---
title: IDebugBreakEvent2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: adfe4bf801d419d2eb25ba2191a180ca261a6c3f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
這個介面會告知工作階段的偵錯管理員 (SDM) 確認已成功完成非同步的中斷。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面可在程式中支援使用者符號。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件上 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 SDM 呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)當使用者已要求要暫停進行偵錯的程式。 當程式已順利暫停時，會將傳送 DE`IDebugBreakEvent2`事件。 此事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，SDM 所提供的回呼函式。  
  
## <a name="remarks"></a>備註  
 例如，使用者可以選取**全部中斷**命令**偵錯**功能表來中斷程式執行無限迴圈。 SDM 會告訴程式停止藉由呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)。 DE 傳送`IDebugBreakEvent2`最後停止程式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)