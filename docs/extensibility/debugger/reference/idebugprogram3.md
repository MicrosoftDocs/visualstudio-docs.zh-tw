---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcc1b6071fbe83b6752b1b2b1ac2218979dbc55f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917061"
---
# <a name="idebugprogram3"></a>IDebugProgram3
此介面代表一個程式正在執行的處理序中，擴充[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)藉由提供執行緒資訊。

## <a name="syntax"></a>語法

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 和自訂的連接埠提供者實作這個介面來代表處理程序中的程式。 工作階段的偵錯管理員 (SDM) 也會實作這個介面來提供資訊給[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。

## <a name="notes-for-callers"></a>呼叫端資訊
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會傳回此新的程式的介面。 此介面也做為參數的多個介面上的許多方法。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgram3`。

|方法|描述|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|執行程式。 執行緒會傳回給哪一個執行緒執行時，正在檢視使用者的偵錯工具資訊。|

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>備註
 程式是處理程序組成一或多個程式時，在特定的執行階段架構中，執行的執行緒容器。

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)