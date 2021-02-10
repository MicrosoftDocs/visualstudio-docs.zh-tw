---
title: IDebugBreakpointEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d2076f4c98748d33542b4457f236711c38936aea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952300"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
當程式在中斷點停止時，debug engine (DE) 會將這個介面傳送至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 在中斷點的支援過程中，會將此介面實作為一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 使用[QueryInterface](/cpp/atl/queryinterface)來存取 `IDebugEvent2` 介面) 。

## <a name="notes-for-callers"></a>呼叫者注意事項
 當程式中至少有一個中斷點時，[取消] 會建立並傳送此事件物件。 當附加至要進行偵錯工具的程式時，會使用由 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugBreakpointEvent2` 。

|方法|描述|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|針對在目前程式碼位置引發的所有中斷點建立枚舉器。|

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
