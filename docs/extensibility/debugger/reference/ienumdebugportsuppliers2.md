---
title: IEnumDebugPort供應商2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715931"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
此介面枚舉埠供應商。

## <a name="syntax"></a>語法

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 實現此介面以表示埠供應商的清單。

## <a name="notes-for-callers"></a>通話備註
 致電[EnumPort 供應商](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)以獲取港口供應商清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugPortSuppliers2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|在枚舉序列中檢索指定數量的埠供應商。|
|[跳](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|在枚舉序列中跳過指定數量的埠供應商。|
|[重設](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|獲取枚舉器中的埠供應商數。|

## <a name="remarks"></a>備註
 調試引擎通常不需要獲取此介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
