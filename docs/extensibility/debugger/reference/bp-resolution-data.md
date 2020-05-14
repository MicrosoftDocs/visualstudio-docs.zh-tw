---
title: BP_RESOLUTION_DATA |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737835"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
描述綁定數據斷點的結果。

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
已綁定的數據表達式。

`bstrFunc`\
數據斷點綁定的函數的名稱(如果有)。

`bstrImage`\
數據斷點繫結定的模組名稱(例如 MyModule.dll)。

`dwFlags`\
[BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)枚舉中的值,描述數據斷點是如何實現的。

## <a name="remarks"></a>備註
此結構是[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)結構的成員,該結構依次是[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)方法返回[的BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
