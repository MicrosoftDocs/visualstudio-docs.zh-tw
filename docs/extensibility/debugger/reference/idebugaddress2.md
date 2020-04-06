---
title: IDebug位址2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 402d8c8bcb50c570ff680b8fe1cf8d26f037ba17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736565"
---
# <a name="idebugaddress2"></a>IDebugAddress2
此介面提供對擁有其位址由此介面表示的物件的進程 ID 的訪問。

## <a name="syntax"></a>語法

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面的同一對象上實現此介面。 此介面提供對擁有與此位址相關的物件的進程的ID的訪問。

## <a name="notes-for-callers"></a>通話備註
 使用[查詢介面](/cpp/atl/queryinterface)從[IDebug 位址](../../../extensibility/debugger/reference/idebugaddress.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>可 v 可排序方法
 除了從[IDebugAddress 介面](../../../extensibility/debugger/reference/idebugaddress.md)繼承的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|檢索擁有此介面表示的對象的進程的ID。|

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
