---
title: IDebugcanStopevent2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734518"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
此介面用於詢問工作階段除錯管理員 (SDM) 是否在目前的程式碼位置停止。

## <a name="syntax"></a>語法

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以支援單步執行原始碼。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

 此介面的實現必須將 SDM 的[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)調用傳達到調試引擎。 例如,這可以通過發佈到調試引擎的消息處理線程的消息來完成,或者實現此介面的物件可以保留對調試引擎的引用,並在將標誌傳遞`IDebugCanStopEvent2::CanStop`到 調試引擎時調用回調試引擎。

## <a name="notes-for-callers"></a>通話備註
 每次要求 DE 繼續執行 DE 並且 DE 正在單步執行代碼時,DE 都可以發送此方法。 此事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugCanStopEvent2`。

|方法|描述|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|獲取此事件的原因。|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|指定正在除錯的程式應在此事件的位置停止(並發送描述停止原因的事件)還是繼續執行。|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|獲取描述此事件位置的文檔上下文。|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|獲取描述此事件位置的代碼上下文。|

## <a name="remarks"></a>備註
 如果使用者踏入函數,並且 DE 發現不存在調試資訊或存在調試資訊,則 DE 會發送此介面,但 DE 不知道是否可以為該位置顯示原始碼。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
