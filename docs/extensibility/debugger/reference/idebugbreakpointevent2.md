---
title: IDebug 突破點事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f59bdef49f5c7b9c4dc345ba1862f3f08042428e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735023"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
當程式停止在斷點時,調試引擎 (DE) 會將此介面發送到工作階段調試管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面作為其對斷點的支援的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

## <a name="notes-for-callers"></a>通話備註
 當程式中遇到至少一個斷點時,DE 將創建併發送此事件物件。 該事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointEvent2`。

|方法|描述|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|為在當前代碼位置觸發的所有斷點創建枚舉器。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
