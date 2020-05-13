---
title: BPREQI_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737744"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
指定要檢索的關於斷點請求的資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="fields"></a>欄位
`BPREQI_BPLOCATION`\
初始化/使用`bpLocation`[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)或[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的(斷點位置)欄位。

`BPREQI_LANGUAGE`\
初始化/使用`guidLanguage``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_PROGRAM`\
初始化/使用`pProgram``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_PROGRAMNAME`\
初始化/使用`bstrProgramName``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_THREAD`\
初始化/使用`pThread``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_THREADNAME`\
初始化/使用`bstrThreadName``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_PASSCOUNT`\
初始化/使用`bpPassCount``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_CONDITION`\
初始化/使用`bpCondition``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的(斷點條件)欄位。

`BPREQI_FLAGS`\
初始化/使用`dwFlags``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI_ALLOLDFIELDS`\
初始化/使用`BP_REQUEST_INFO`結構的所有欄位。

`BPREQI_VENDOR`\
初始化/使用結構`guidVendor`欄位`BP_REQUEST_INFO2`。

`BPREQI_CONSTRAINT`\
初始化/使用結構`bstrConstraint`欄位`BP_REQUEST_INFO2`。

`BPREQI_TRACEPOINT`\
初始化/使用結構`bstrTracepoint`欄位`BP_REQUEST_INFO2`。

`BPREQI_ALLFIELDS`\
指定`BP_REQUEST_INFO2`結構的所有欄位。

## <a name="remarks"></a>備註
作為參數傳遞給[GetRequestInfo,](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)[並BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)方法指定要初始化[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的欄位。

這些標誌還用於指示返回每個結構時使用`BP_REQUEST_INFO`和`BP_REQUEST_INFO2`結構的欄位並有效。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
