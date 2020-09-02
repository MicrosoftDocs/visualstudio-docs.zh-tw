---
title: IEnumDebugPortSuppliers2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715931"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
此介面會列舉埠供應商。

## <a name="syntax"></a>語法

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Visual Studio 會執行此介面來代表埠供應商的清單。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 來取得埠供應商的清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugPortSuppliers2` 。

|方法|描述|
|------------|-----------------|
|[下一個](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|以列舉順序抓取指定的埠供應商數目。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|略過列舉序列中指定的埠供應商數目。|
|[重設](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|取得枚舉器中的埠供應商數目。|

## <a name="remarks"></a>備註
 Debug engine 通常不需要取得這個介面。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
