---
title: IDebugFunctionPosition2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e05cc09d2c252ddeaadc3cfa1b40e1a5797b6d79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920908"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
此介面表示函式在來源文件中的抽象位置。

## <a name="syntax"></a>Syntax

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表函數在來源文件中的位置。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面會當做 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 聯集的一部分來提供 (具體而言，就是在建立暫止中斷點時所用的 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 結構) ，它會成為 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 結構的一部分。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugFunctionPosition2` 。

|方法|描述|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|取得此位置相對的函式名稱。|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|取得函數開頭的位移。|

## <a name="remarks"></a>備註
 這個介面所表示的位置是以文字為基礎，特別是 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 結構。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
