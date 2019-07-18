---
title: IDebugEngine2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c011a530bbd4323546257a40334a4b8a0f57bdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195903"
---
# <a name="idebugengine2"></a>IDebugEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會表示偵錯引擎 (DE)。 它用來管理各方面的偵錯工作階段中，從建立中斷點，設定及清除例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 實作這個介面是由管理程式的偵錯自訂的規定。 此介面必須由 DE 實作。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是由工作階段的偵錯管理員 (SDM) 來管理偵錯工作階段，包括管理例外狀況、 建立中斷點，以及回應裝置所傳送的事件同步呼叫。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEngine2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|建立所有正在偵錯程式所規定的列舉值。|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|附加至程式的規定。|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE 中建立暫止中斷點。|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|指定 DE 應該如何處理指定的例外狀況。|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|移除指定的例外狀況，讓它不再由偵錯引擎。|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|移除 IDE 已設定特定的執行階段架構或語言的例外狀況的清單。|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|取得 DE 的 GUID。|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|會通知 DE 4mb 已終止指定的程式和 DE 應該清除至程式的所有參考，並傳送程式損毀的事件。|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|表示同步的偵錯事件，先前傳送給 SDM，德國已收到並處理 SDM 由呼叫。|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|設定預設的地區設定。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|DE 使用目前設定的登錄根目錄。|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|設定計量。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|所有由這個 DE 正在偵錯的程式停止執行的其中一個其執行緒嘗試執行下一次要求。|  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
