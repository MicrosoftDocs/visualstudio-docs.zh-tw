---
description: 此介面會列舉機器或埠供應商的埠。
title: IEnumDebugPorts2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66598460a48c960b78cb89315fff6bd7ac9a845e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064588"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
此介面會列舉機器或埠供應商的埠。

## <a name="syntax"></a>Syntax

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂埠供應商會執行這個介面，以代表供應商所建立的埠清單。 Visual Studio 將此介面實作為其本身的埠供應商的支援。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 以取得此介面，此介面代表埠供應商所建立的埠清單。 呼叫 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) 以取得此介面，此介面代表已儲存至磁片的埠清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugPorts2` 。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|以列舉順序抓取指定的埠數目。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|略過列舉序列中指定的埠數目。|
|[重設](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|取得枚舉器中的埠數目。|

## <a name="remarks"></a>備註
 Visual Studio 使用此介面來協助填入用於附加至進程的埠清單。

 Debug engine 通常不會使用此介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
