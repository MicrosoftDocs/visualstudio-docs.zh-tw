---
title: IDebugProgramDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c0f4e3f11ad10787e8627ba0250ff1480dfb994
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697430"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
這個介面會傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 當程式執行到完成。

## <a name="syntax"></a>語法

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 或自訂的連接埠提供者會實作這個介面來報告程式已終止，且不再可供偵錯。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面。

## <a name="notes-for-callers"></a>呼叫端資訊
 DE 或自訂的連接埠提供者會建立並傳送這個事件来報告的物件終止程式。 DE 使用傳送這個事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。 此事件使用自訂的連接埠提供者將傳送[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramDestroyEvent2`。

|方法|描述|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|取得程式的結束代碼。|

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)