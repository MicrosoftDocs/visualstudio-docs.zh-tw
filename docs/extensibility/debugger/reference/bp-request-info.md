---
description: 包含執行中斷點所需的資訊。
title: BP_REQUEST_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40c88d1c07d3610ff6d098fbbf8517476cc07103
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059648"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
包含執行中斷點所需的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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

## <a name="remarks"></a>備註
[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)方法會傳回這個結構。

如果您需要取得 debug engine 廠商 GUID、中斷點條件約束或追蹤點，請參閱 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 結構。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
