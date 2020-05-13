---
title: IDebugPort供應商3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724434"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
此介面允許調用方確定埠供應商是否可以在調試器的調用之間保留埠(通過將它們寫入磁碟),然後獲取這些保留的埠的清單。

## <a name="syntax"></a>語法

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商實現此介面以支援保留或將埠資訊保存到磁碟。 此介面必須在與[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面相同的對象上實現。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugPortSupplier2`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 除了從[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面繼承的方法外,此介面還支援以下功能:

|方法|描述|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|返回埠供應商是否可以在調試器的調用之間保留埠(通過將它們寫入磁碟)。|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|返回可用於枚舉此埠供應商寫入磁碟的所有埠的物件。|

## <a name="remarks"></a>備註
 如果埠供應商可以跨調用保留埠,則應實現此介面。 當埠供應商實例化時,應載入埠,並在埠供應商銷毀時寫入磁碟。

 調試引擎通常不與埠供應商交互,並且對此介面沒有用處。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
