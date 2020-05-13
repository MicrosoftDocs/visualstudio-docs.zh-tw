---
title: BPREQI_FIELDS90 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737743"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
枚舉指定要檢索的關於斷點請求的資訊的有效值。 此枚舉擴展了[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)枚舉。

## <a name="syntax"></a>語法

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>欄位
`BPREQI90_BPLOCATION`\
初始化或使用[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)BP_REQUEST_INFO`bpLocation`或[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的(斷點位置)欄位。

`BPREQI90_LANGUAGE`\
初始化或使用`guidLanguage``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_PROGRAM`\
初始化或使用`pProgram``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_PROGRAMNAME`\
初始化或使用`bstrProgramName``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_THREAD`\
初始化或使用`pThread``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_THREADNAME`\
初始化或使用`bstrThreadName``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_PASSCOUNT`\
初始化或使用`bpPassCount``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_CONDITION`\
初始化或使用`bpCondition``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的(斷點條件)欄位。

`BPREQI90_FLAGS`\
初始化或使用`dwFlags``BP_REQUEST_INFO``BP_REQUEST_INFO2`或結構的欄位。

`BPREQI90_ALLOLDFIELDS`\
初始化或使用`BP_REQUEST_INFO`結構的所有欄位。

`BPREQI90_VENDOR`\
初始化或使用結構`guidVendor`欄位`BP_REQUEST_INFO2`。

`BPREQI90_CONSTRAINT`\
初始化或使用結構`bstrConstraint`欄位`BP_REQUEST_INFO2`。

`BPREQI90_TRACEPOINT`\
初始化或使用結構`bstrTracepoint`欄位`BP_REQUEST_INFO2`。

`BPREQI90_MACROTRACEPOINT`\
初始化或使用結構`bstrMacroTracepoint`欄位`BP_REQUEST_INFO2`。 BPREQI_ALLFIELDS不包括此欄位。

`BPREQI90_ALLFIELDS`\
指定`BP_REQUEST_INFO2`結構的所有欄位。

## <a name="requirements"></a>需求
標題: Msdbg90.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
