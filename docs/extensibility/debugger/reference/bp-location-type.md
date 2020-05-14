---
title: BP_LOCATION_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737949"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
指定斷點請求的斷點的位置類型。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>欄位
`BPLT_NONE`\
指定無斷點位置。

`BPLT_FILE_LINE`\
指定斷點的位置類型作為檔行。

`BPLT_FUNC_OFFSET`\
指定斷點的位置類型作為函數偏移。

`BPLT_CONTEXT`\
指定斷點作為上下文的位置類型。

`BPLT_STRING`\
指定斷點作為字串的位置類型。

`BPLT_ADDRESS`\
指定斷點作為位址的位置類型。

`BPLT_RESOLUTION`\
將斷點的位置類型指定為解析度。

`BPLT_CODE_FILE_LINE`\
指定斷點的位置類型作為原始碼行。

`BPLT_CODE_FUNC_OFFSET`\
指定斷點的位置類型作為代碼函數偏移量。

`BPLT_CODE_CONTEXT`\
指定斷點作為代碼上下文的位置類型。

`BPLT_CODE_STRING`\
指定斷點的位置類型作為代碼字串。

`BPLT_CODE_ADDRESS`\
指定斷點的位置類型作為代碼位址。

`BPLT_DATA_STRING`\
指定斷點作為資料字串的位置類型。

`BPLT_TYPE_MASK`\
指定位掩碼,以便可以從值中提取斷點類型。

`BPLT_LOCATION_TYPE_MASK`\
指定位掩碼,以便可以從值中提取斷點位置類型。

## <a name="remarks"></a>備註
作為參數傳遞給[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)方法。

斷點位置類型由斷點類型和位置類型組成。 這意味著斷點位置類型絕不只是斷點類型(例如`BPT_CODE`)或位置類型(例如)。 `BPLT_FILE_LINE` 當前支援的所有斷點位置類型的預定義常量都包含在此枚舉`BPLT_CODE_FILE_LINE`(`BPLT_DATA_STRING`通過 ) 中。

`BPT_CODE`是`BPT_DATA`[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)枚舉的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
