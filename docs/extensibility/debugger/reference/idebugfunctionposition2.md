---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19b9fbe16abec97ef29794b66cc4fe92631ca0af
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313246"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
此介面代表來源文件中的函式的抽象位置。

## <a name="syntax"></a>語法

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面來代表來源文件內的函式的位置。

## <a name="notes-for-callers"></a>呼叫端資訊
 這個介面會提供一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (具體而言， [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)結構)，接著是一部分[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構，用來建立暫止中斷點。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugFunctionPosition2`。

|方法|描述|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|取得這個位置就是相對於函式的名稱。|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|取得函式開頭的位移。|

## <a name="remarks"></a>備註
 此介面所代表的位置是文字為基礎，特別是， [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)