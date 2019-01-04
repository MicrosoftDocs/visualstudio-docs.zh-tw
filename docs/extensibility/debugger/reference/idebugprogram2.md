---
title: IDebugProgram2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7ee7d44d6087ea53cf0ae063ce3bcb7473157aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826175"
---
# <a name="idebugprogram2"></a>IDebugProgram2
這個介面會表示執行的處理序中的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 和自訂的連接埠提供者實作這個介面來代表處理程序中的程式。 工作階段的偵錯管理員 (SDM) 也會實作這個介面來提供資訊給[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會傳回此新的程式的介面。 此介面也做為參數的多個介面上的許多方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProgram2`。  
  
|方法|描述|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|列舉在此程式中執行的執行緒。|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|取得程式的名稱。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|取得此程式正在執行中的程序。|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|終止這個程式。|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|將附加至這個程式。|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|決定偵錯引擎 (DE) 可以中斷連結程式。|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|此程式的偵錯工具會中斷連結。|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|取得此程式的全域唯一識別碼。|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|取得程式內容。|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|會繼續執行此程式從已停止的狀態。 會清除任何先前的執行狀態。|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|會繼續執行此程式從已停止的狀態。 會保留任何先前的執行狀態。|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|會執行的步驟。|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|此程式停止執行下一個要求的時間其執行緒執行的程式碼的其中一個。|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|取得執行此程式的偵錯引擎 (DE) 的識別碼與名稱。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|列舉在原始程式檔中的指定位置的程式碼內容。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|取得此程式的記憶體位元組。|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|取得此程式或此計劃的一部分反組譯碼資料流。|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|列舉，此程式已載入，並且正在執行的模組。|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|取得此程式的 編輯後繼續 (ENC) 更新。<br /><br /> 自訂的偵錯引擎不會實作這個方法 (它應該會一律傳回`E_NOTIMPL`)。|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|列舉此程式的程式碼路徑。|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|寫入檔案中的傾印。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>備註  
 程式是處理程序組成一或多個程式時，在特定的執行階段架構中，執行的執行緒容器。  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)