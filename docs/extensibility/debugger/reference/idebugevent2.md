---
description: 這個介面是用來傳達重要的偵錯工具資訊，例如在中斷點停止，以及非關鍵的資訊，例如偵錯工具訊息。
title: IDebugEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5406c70703b594236dba47539e5cc76bbe67a73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065758"
---
# <a name="idebugevent2"></a>IDebugEvent2
這個介面是用來傳達重要的偵錯工具資訊，例如在中斷點停止，以及非關鍵的資訊，例如偵錯工具訊息。

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 和自訂埠供應商會在與所有其他事件介面相同的物件上執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 使用指定給 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 或 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)的介面識別碼 (IID) 引數，會話 debug manager (SDM) 會呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` ，以取得適當的事件介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|取得這個 debug 事件的屬性。|

## <a name="remarks"></a>備註
 更特定的事件介面（例如 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)）不會衍生自 IDebugEvent2 介面，但會改為在與相同的物件上實作為個別的介面 `IDebugEvent2` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
