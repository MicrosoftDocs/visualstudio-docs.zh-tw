---
title: BP_ERROR_RESOLUTION_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738093"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
描述錯誤斷點的解析度,包括位置、程式和線程。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>成員
`dwFields`\
[BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)枚舉中的值的組合,指定填充此結構的欄位。

`bpResLocation`\
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)聯合,它指定斷點解析位置。

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示發生斷點錯誤的應用程式。

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件,表示生成斷點錯誤的應用程式在其上運行的線程。

`bstrMessage`\
包含此錯誤解決方法引起的任何警告或錯誤訊息的字串。

`dwType`\
[BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)枚舉中指定斷點錯誤類型的值。

## <a name="remarks"></a>備註
此結構從[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
