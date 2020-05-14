---
title: IEnum調試埠2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716111"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
此介面枚舉機器或埠供應商的埠。

## <a name="syntax"></a>語法

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商實現此介面以表示供應商創建的埠清單。 Visual Studio 實現此介面以支援其自己的埠供應商。

## <a name="notes-for-callers"></a>通話備註
 呼叫[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)以獲取此介面,表示埠供應商創建的埠清單。 呼叫[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)以取得此介面,表示保存到磁碟的埠清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugPorts2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|檢索枚舉序列中指定數量的埠。|
|[跳](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|在枚舉序列中跳過指定數量的埠。|
|[重設](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|獲取枚舉器中的埠數。|

## <a name="remarks"></a>備註
 Visual Studio 使用此介面幫助填充用於附加到進程的埠清單。

 調試引擎通常不使用此介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
