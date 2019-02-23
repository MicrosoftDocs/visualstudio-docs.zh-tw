---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f4f01bb8e86e733bef3940a4772f52b28080628
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712381"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
此介面用來代表，並從網路上的機器上的伺服器取得資訊。

## <a name="syntax"></a>語法

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 Visual Studio 會實作這個介面來代表伺服器。 Visual Studio 的每個執行個體建立這個介面的執行個體。

## <a name="notes-for-callers"></a>呼叫端資訊
 自訂連接埠供應商收到的呼叫中的這個介面[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。

 偵錯引擎可以獲得這個介面，透過呼叫間接[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (它會傳回[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)，衍生自介面`IDebugCoreServer2`)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugCoreServer2`。

|方法|描述|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|取得機器的屬性與名稱。|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|取得機器的名稱。|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|取得連接埠提供者存在於電腦上。|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|取得已經存在電腦的連接埠。|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|機器上建立的所有連接埠的列舉值。|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|機器上建立所有連接埠提供者的列舉值。|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|取得機器的機器的公用程式。|

## <a name="remarks"></a>備註
 Visual Studio 也會使用此介面來瀏覽網路上的機器上執行的處理序。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)