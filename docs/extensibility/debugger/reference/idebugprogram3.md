---
title: IDebugProgram3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722638"
---
# <a name="idebugprogram3"></a>IDebugProgram3
此介面表示在進程中運行的程式,並通過提供線程資訊擴展[Execute。](../../../extensibility/debugger/reference/idebugprogram2-execute.md)

## <a name="syntax"></a>語法

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 和自訂埠供應商實現此介面以表示進程中的程式。 會話調試管理員 (SDM) 還實現此介面,以向[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)提供資訊。

## <a name="notes-for-callers"></a>通話備註
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件返回新程式的此介面。 此介面還用作多個介面上許多方法的參數。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgram3`。

|方法|描述|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|執行程式。 返回線程以向調試器提供有關使用者在執行時正在查看的線程的資訊。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="remarks"></a>備註
 程式是在特定的運行時體系結構中運行的線程容器,而進程由一個或多個程序組成。

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
