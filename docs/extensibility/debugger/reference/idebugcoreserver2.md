---
title: IDebugCoreServer2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733031"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
此介面用於表示和獲取網路上的電腦上的伺服器的資訊。

## <a name="syntax"></a>語法

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 實現此介面以表示伺服器。 Visual Studio 的每個實例都創建此介面的實例。

## <a name="notes-for-callers"></a>通話備註
 自定義埠供應商在調用[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)中接收此介面。

 除錯引擎可以透過調用[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)間接取得此介面(它傳回[IDebugCoreServer3,](../../../extensibility/debugger/reference/idebugcoreserver3.md)一個派生自`IDebugCoreServer2`的介面)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugCoreServer2`。

|方法|描述|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|獲取計算機的名稱和屬性。|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|獲取計算機的名稱。|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|獲取電腦上存在的埠供應商。|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|獲取計算機上已存在的埠。|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|為電腦上的所有埠創建枚舉器。|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|為電腦上的所有埠供應商創建枚舉器。|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|獲取機器的機器實用程式。|

## <a name="remarks"></a>備註
 Visual Studio 還使用此介面來瀏覽在網路上運行的進程。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
