---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79104bf245221c14a27593665c1a4b2cd8cedaa0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707220"
---
# <a name="bpresolutioninfo"></a>BP_RESOLUTION_INFO
描述程式碼中斷點或資料中斷點的繫結的中斷點資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>成員
`dwFields` 集合中的旗標[BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)列舉，指定哪些欄位都已填寫。

`bpResLocation` [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)結構，程式碼或資料中指定之中斷點的位置。

`pProgram` [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示中斷點錯誤發生所在的應用程式。

`pThread` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示包含中斷點錯誤的應用程式執行所在的執行緒。

## <a name="remarks"></a>備註
此結構由[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
