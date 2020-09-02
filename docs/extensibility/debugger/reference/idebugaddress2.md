---
title: IDebugAddress2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736565"
---
# <a name="idebugaddress2"></a>IDebugAddress2
這個介面可讓您存取擁有物件之進程的識別碼，該物件的位址由這個介面表示。

## <a name="syntax"></a>語法

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會在執行 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面的相同物件上，執行這個介面。 這個介面可讓您存取擁有與此位址相關之物件的進程識別碼。

## <a name="notes-for-callers"></a>呼叫者注意事項
 使用 [QueryInterface](/cpp/atl/queryinterface) 從 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面取得這個介面。

## <a name="methods-in-vtable-order"></a>採用 vtable 順序的方法
 除了繼承自 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面的方法之外，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|抓取擁有這個介面所表示之物件的進程識別碼。|

## <a name="requirements"></a>需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
