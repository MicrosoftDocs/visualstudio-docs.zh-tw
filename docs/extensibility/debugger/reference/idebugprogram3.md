---
title: IDebugProgram3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d22a58021a744cc71b8df3acb8e577d853aa2829
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889989"
---
# <a name="idebugprogram3"></a>IDebugProgram3
這個介面代表在進程中執行的程式，並藉由提供執行緒資訊來擴充 [執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md) 。

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) ，而自訂埠供應商會執行此介面來代表進程中的程式。 會話 debug manager (SDM) 也會執行這個介面，以提供要 [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)的資訊。

## <a name="notes-for-callers"></a>呼叫者注意事項
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會為新程式傳回這個介面。 這個介面也會當做多個介面上許多方法的參數使用。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProgram3` 。

|方法|描述|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|執行程式。 傳回的執行緒可提供偵錯工具資訊給使用者在執行時所要查看的執行緒。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>備註
 程式是在特定執行時間架構中執行的執行緒容器，而處理常式是由一或多個程式所組成。

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
