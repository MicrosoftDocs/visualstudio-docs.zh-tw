---
title: IDebug 突破點無綁定事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e1d15936316d08a712e3d6f3fdc7a3a73be613d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734633"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
此介面告訴工作階段調試管理器 (SDM),綁定斷點已未綁定到已載入的程式。

## <a name="syntax"></a>語法

```
IDebugBreakpointUnboundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其對斷點的支援的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

## <a name="notes-for-callers"></a>通話備註
 當綁定斷點未綁定時,DE 將創建併發送此事件物件。 該事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointUnboundEvent2`。

|方法|描述|
|------------|-----------------|
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|獲取非綁定的斷點。|
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|獲取斷點未綁定的原因。|

## <a name="remarks"></a>備註
 當調試引擎 DLL 或類卸載時,綁定到該模組中代碼的所有斷點都必須與正在調試的程式取消綁定。 指定未`IDebugBreakpointUnboundEvent2`結合的斷點 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
