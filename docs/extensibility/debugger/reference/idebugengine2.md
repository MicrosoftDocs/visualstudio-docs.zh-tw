---
title: IDebugEngine2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2cfe7e2f54b45ecfe8fdb34943b87818a13feab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2"></a>IDebugEngine2
此介面代表偵錯引擎 (DE)。 它用來建立中斷點來設定及清除例外狀況中管理的偵錯工作階段，各層面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 此介面是由管理程式的偵錯自訂 DE 實作。 DE 必須實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是由工作階段的偵錯管理員 (SDM) 來管理偵錯工作階段，包括管理例外狀況、 建立中斷點，以及回應 DE 所傳送的事件同步呼叫。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEngine2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|建立偵錯程式 DE 的所有程式的列舉值。|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|將 DE 附加至程式。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE 中建立的暫止中斷點。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|指定 DE 應該如何處理指定的例外狀況。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|移除指定的例外狀況，讓它不再由偵錯引擎。|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|移除 IDE 已經設定為特定的執行階段架構或語言的例外狀況的清單。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|取得 DE 的 GUID。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|通知 DE 4mb 終止指定的程式，而且 DE 應該清除程式的所有參考，並傳送程式損毀事件。|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|呼叫以表示同步偵錯事件，先前傳送到 SDM DE 已接收並處理 SDM。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|設定 DE 的地區設定。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|使用 DE 目前設定的登錄根目錄。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|設定計量。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|所有由這個 DE 偵錯的程式停止執行其中一個其執行緒嘗試執行下一次要求。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)