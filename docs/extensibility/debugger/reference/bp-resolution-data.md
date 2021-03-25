---
description: 描述系結資料中斷點的結果。
title: BP_RESOLUTION_DATA |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 848a2b22ece8d3a51d7eef28b1f8baa7164ca22d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054708"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
描述系結資料中斷點的結果。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>成員
`bstrDataExpr`\
已系結的日期運算式。

`bstrFunc`\
如果有任何) ，資料中斷點在 (中系結的函數名稱。

`bstrImage`\
 (MyModule.dll 的模組名稱，例如資料中斷點已系結的) 。

`dwFlags`\
[BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)列舉中的值，描述資料中斷點的執行方式。

## <a name="remarks"></a>備註
此結構是[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)結構的成員，它會接著[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)方法所傳回之[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構的成員。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
