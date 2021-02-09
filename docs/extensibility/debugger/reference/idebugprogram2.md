---
title: IDebugProgram2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c262f123e56bf9ed9751ad8b9e7d91770cbd2df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887103"
---
# <a name="idebugprogram2"></a>IDebugProgram2
這個介面代表在進程中執行的程式。

## <a name="syntax"></a>Syntax

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) ，而自訂埠供應商會執行此介面來代表進程中的程式。 會話 debug manager (SDM) 也會執行這個介面，以提供要 [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)的資訊。

## <a name="notes-for-callers"></a>呼叫者注意事項
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會為新程式傳回這個介面。 這個介面也會當做多個介面上許多方法的參數使用。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProgram2` 。

|方法|描述|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|列舉在此程式中執行的執行緒。|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|取得程式的名稱。|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|取得此程式正在其中執行的進程。|
|[終止](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|終止此程式。|
|[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|附加至此程式。|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|決定 debug engine (DE) 是否可以與程式中斷連結。|
|[卸離](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|從這個程式卸離偵錯工具。|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|取得此程式的全域唯一識別碼。|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|取得程式屬性。|
|[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|從停止狀態繼續執行此程式。 任何先前的執行狀態都會清除。|
|[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|從停止狀態繼續執行此程式。 任何先前的執行狀態都會保留下來。|
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|執行步驟。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|要求此程式會在下一個執行緒執行程式碼時停止執行。|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|取得在執行此程式時， (DE) 的偵測引擎的名稱和識別碼。|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|列舉原始程式檔中指定位置的程式碼內容。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|取得此程式的記憶體位元組。|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|取得此程式的反組解碼資料流程或此程式的一部分。|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|列舉這個程式已載入並正在執行的模組。|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|取得此程式的 [編輯後繼續] (ENC) 更新。<br /><br /> 自訂的調試引擎不會執行此方法 (它應該一律傳回 `E_NOTIMPL`) 。|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|列舉此程式的程式碼路徑。|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|將傾印寫入檔案。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>備註
 程式是在特定執行時間架構中執行的執行緒容器，而處理常式是由一或多個程式所組成。

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
