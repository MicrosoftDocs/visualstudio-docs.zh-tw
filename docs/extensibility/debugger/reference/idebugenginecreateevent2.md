---
title: IDebugEngine創建事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a964f1e08fc2e88ac9a1d211e4b3e36b32c5b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730606"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
創建 DE 實例時,除錯引擎 (DE) 會將此介面發送到工作階段調試管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面作為其正常操作的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM`QueryInterface``IDebugEvent2`使用方法 存取介面)。

## <a name="notes-for-callers"></a>通話備註
 DE 在 DE 實例化後創建並發送此事件物件。 該事件使用 SDM 在連接到正在調試的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數進行發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEngineCreateEvent2`。

|方法|描述|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|檢索表示新創建的調試引擎 (DE) 的物件。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
