---
description: 包含執行中斷點所需的資訊，包括廠商 GUID、條件約束和追蹤點。
title: BP_REQUEST_INFO2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1efeceb42d45822f232e5a2e5e2fbe33f9996e34
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144113"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
包含執行中斷點所需的資訊，包括廠商 GUID、條件約束和追蹤點。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>成員
`dwFields`\
[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)列舉中的旗標組合，可指定要填寫的欄位。

`guidLanguage`\
語言 GUID。

`bpLocation`\
指定中斷點位置類型的 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 結構。

`pProgram`\
代表中斷點發生所在之應用程式的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件。

`bstrProgramName`\
發生中斷點的應用程式名稱。

`pThread`\
代表中斷點發生所在之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

`bstrThreadName`\
發生中斷點的執行緒名稱。

`bpCondition`\
描述中斷點將引發之條件的 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 結構。

`bpPassCount`\
包含中斷點之傳遞計數資訊的 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 結構。

`dwFlags`\
[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)列舉中的旗標組合，可指定所要求中斷點的旗標。

`guidVendor`\
廠商的 GUID。 可以是 null 值。

`bstrConstraint`\
中斷點條件約束的名稱。 可以是 null 值。

`bstrTracepoint`\
追蹤點的名稱。 可以是 null 值。

## <a name="remarks"></a>備註
[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)方法會傳回這個結構。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
