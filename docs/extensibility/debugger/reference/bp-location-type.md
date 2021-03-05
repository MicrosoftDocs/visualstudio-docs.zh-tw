---
description: 指定中斷點要求之中斷點的位置類型。
title: BP_LOCATION_TYPE |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1ccf81393e42cc79b0ef93703b4a2327207baf6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144191"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
指定中斷點要求之中斷點的位置類型。

## <a name="syntax"></a>Syntax

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
指定無中斷點位置。

`BPLT_FILE_LINE`\
以檔案行指定中斷點的位置類型。

`BPLT_FUNC_OFFSET`\
以函數位移的形式指定中斷點的位置類型。

`BPLT_CONTEXT`\
將中斷點的位置類型指定為內容。

`BPLT_STRING`\
以字串形式指定中斷點的位置類型。

`BPLT_ADDRESS`\
以位址指定中斷點的位置類型。

`BPLT_RESOLUTION`\
將中斷點的位置類型指定為解析度。

`BPLT_CODE_FILE_LINE`\
將中斷點的位置類型指定為原始程式碼的行。

`BPLT_CODE_FUNC_OFFSET`\
將中斷點的位置類型指定為程式碼函數的位移。

`BPLT_CODE_CONTEXT`\
將中斷點的位置類型指定為程式碼內容。

`BPLT_CODE_STRING`\
將中斷點的位置類型指定為程式碼字串。

`BPLT_CODE_ADDRESS`\
將中斷點的位置類型指定為程式碼位址。

`BPLT_DATA_STRING`\
以資料字串的形式指定中斷點的位置類型。

`BPLT_TYPE_MASK`\
指定位元遮罩，讓中斷點類型可以從值中解壓縮。

`BPLT_LOCATION_TYPE_MASK`\
指定位元遮罩，以便將中斷點位置型別解壓縮出值。

## <a name="remarks"></a>備註
以參數形式傳遞至 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) 方法。

中斷點位置型別是由中斷點型別和位置型別所組成。 這表示，中斷點位置型別絕不只是中斷點類型 (例如 `BPT_CODE`) 或位置類型 (例如 `BPLT_FILE_LINE`) 。 目前支援的所有中斷點位置類型的預先定義常數，都包含在此列舉 (中 `BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING`) 。

`BPT_CODE` 和 `BPT_DATA` 是 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 列舉的成員。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
