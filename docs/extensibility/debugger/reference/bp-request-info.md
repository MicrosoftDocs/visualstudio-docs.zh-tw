---
title: BP_REQUEST_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35a1202f4990f4f6370ad031c896ba85ebb6d816
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737892"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
包含實現斷點所需的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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
[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)枚舉中的標誌的組合,用於指定填寫哪些欄位。

`guidLanguage`\
語言 GUID。

`bpLocation`\
指定斷點位置類型的[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構。

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示發生斷點的應用程式。

`bstrProgramName`\
發生斷點的應用程式的名稱。

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件,表示發生斷點的線程。

`bstrThreadName`\
發生斷點線程的名稱。

`bpCondition`\
描述斷點觸發條件[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)結構。

`bpPassCount`\
包含斷點通過計數資訊的[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)結構。

`dwFlags`\
BP_FLAGS[枚舉](../../../extensibility/debugger/reference/bp-flags.md)中的標誌的組合,用於指定請求的斷點的標誌。

## <a name="remarks"></a>備註
此結構由[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)方法返回。

如果需要獲取調試引擎供應商 GUID、斷點約束或追蹤點,請參閱[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

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
