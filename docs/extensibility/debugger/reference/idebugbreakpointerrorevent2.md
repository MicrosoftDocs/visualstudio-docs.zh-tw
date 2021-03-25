---
description: 此介面會告知會話 debug manager (SDM) 暫止的中斷點無法系結至載入的程式，可能是因為出現警告或錯誤。
title: IDebugBreakpointErrorEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7ebfa6b5d1cc2a0fe1a03c9e70952c5cec1a74e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054525"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
此介面會告知會話 debug manager (SDM) 暫止的中斷點無法系結至載入的程式，可能是因為出現警告或錯誤。

## <a name="syntax"></a>Syntax

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 在中斷點的支援過程中，會將此介面實作為一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 使用[QueryInterface](/cpp/atl/queryinterface)來存取 `IDebugEvent2` 介面) 。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當暫止中斷點無法系結至正在進行偵錯工具的程式時，取消會建立並傳送此事件物件。 當附加至要進行偵錯工具的程式時，會使用由 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugBreakpointErrorEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|取得描述警告或錯誤的 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 介面。|

## <a name="remarks"></a>備註
 每當有中斷點系結時，就會將事件傳送至 SDM。 如果無法系結中斷點， `IDebugBreakpointErrorEvent2` 則會傳送，否則會傳送 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 。

 例如，當與暫止中斷點相關聯的條件無法剖析或評估時，就會傳送警告，指出目前無法系結暫止中斷點。 如果尚未載入中斷點的程式碼，就可能發生這種情況。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
