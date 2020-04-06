---
title: IDebug功能位置2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728317"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
此介面表示源文檔中函數的抽象位置。

## <a name="syntax"></a>語法

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示函數在源文件中的位置。

## <a name="notes-for-callers"></a>通話備註
 此介面作為[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)聯合(特別是[BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)結構)的一部分提供,該聯合是[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構的一部分,用於創建掛起的斷點。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugFunctionPosition2`。

|方法|描述|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|獲取此位置相對的函數的名稱。|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|從函數的開頭獲取偏移量。|

## <a name="remarks"></a>備註
 此介面表示的位置是基於文本的,具體來說,是[一個TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
