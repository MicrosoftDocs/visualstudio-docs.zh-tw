---
description: 此介面可讓呼叫者藉由在偵錯工具的調用間寫入磁片) ，來決定埠供應商是否可以保留埠 (，然後取得這些保留的埠清單。
title: IDebugPortSupplier3 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8db7c2321d5a309f66b85a3f177e20cb3f9b1244
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150389"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
此介面可讓呼叫者藉由在偵錯工具的調用間寫入磁片) ，來決定埠供應商是否可以保留埠 (，然後取得這些保留的埠清單。

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂埠供應商會執行這個介面，以支援將埠資訊保存或儲存至磁片。 這個介面必須在與 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 介面相同的物件上執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 除了繼承自 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 介面的方法之外，此介面還支援下列各項：

|方法|描述|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|傳回埠供應商是否可以透過將埠寫入至) 偵錯工具調用之間的磁片來保存埠 (。|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|傳回物件，這個物件可以用來列舉由此埠供應商寫入磁片的所有埠。|

## <a name="remarks"></a>備註
 如果埠供應商可以跨調用保存埠，則應該執行這個介面。 當埠供應商已具現化時，應載入埠，並在埠供應商終結時寫入磁片。

 Debug engine 通常不會與埠供應商互動，而且不會使用此介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
