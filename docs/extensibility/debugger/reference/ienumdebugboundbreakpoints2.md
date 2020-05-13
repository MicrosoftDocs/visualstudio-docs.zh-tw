---
title: IEnumDebug綁定斷點2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717438"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
此介面枚舉與掛起斷點或斷點綁定事件關聯的綁定斷點。

## <a name="syntax"></a>語法

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其對斷點的支援的一部分。 如果支援斷點,則必須實現此介面。

## <a name="notes-for-callers"></a>通話備註
 視覺工作室呼叫:

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)以獲取此介面,表示觸發的所有斷點的清單。

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)以獲取此介面,表示綁定的所有斷點的清單。

- [EnumBoundBreakpoint](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)以獲取此介面,表示綁定到該掛起斷點的的所有斷點的清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugBoundBreakpoints2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|檢索枚舉序列中指定數量的綁定斷點。|
|[跳](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|在枚舉序列中跳過指定數量的綁定斷點。|
|[重設](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|獲取枚舉器中的綁定斷點數。|

## <a name="remarks"></a>備註
 Visual Studio 使用此介面表示的綁定斷點來更新 IDE 中斷點的顯示。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
