---
title: IDebugProgram2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722727"
---
# <a name="idebugprogram2"></a>IDebugProgram2
此介面表示進程中運行的程式。

## <a name="syntax"></a>語法

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 和自訂埠供應商實現此介面以表示進程中的程式。 會話調試管理員 (SDM) 還實現此介面,以向[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)提供資訊。

## <a name="notes-for-callers"></a>通話備註
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件返回新程式的此介面。 此介面還用作多個介面上許多方法的參數。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgram2`。

|方法|描述|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|枚舉此程式中運行的線程。|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|獲取程式的名稱。|
|[抓取程序](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|獲取此程式正在運行的進程。|
|[終止](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|終止此程式。|
|[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|附加到此程式。|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|確定調試引擎 (DE) 是否可以從程式分離。|
|[中斷連結](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|從該程式分離調試器。|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|獲取此程式的全域唯一標識符。|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|獲取程序屬性。|
|[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|繼續從已停止狀態運行此程式。 清除任何以前的執行狀態。|
|[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|繼續從已停止狀態運行此程式。 保留任何以前的執行狀態。|
|[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)|執行步驟。|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|請求下次其線程運行代碼時停止執行此程式。|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|取得執行此程式的除錯引擎 (DE) 的名稱和識別碼。|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|枚舉源檔中給定位置的代碼上下文。|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|獲取此程式的記憶體位元組。|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|獲取此程式或此程式的一部分的拆解流。|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|枚舉此程式已載入並正在執行的模組。|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|獲取此程式的編輯和繼續 (ENC) 更新。<br /><br /> 自定義調試引擎不實現此方法(應始終返回`E_NOTIMPL`)。|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|枚舉此程式的代碼路徑。|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|將轉儲寫入檔。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="remarks"></a>備註
 程式是在特定的運行時體系結構中運行的線程容器,而進程由一個或多個程序組成。

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
