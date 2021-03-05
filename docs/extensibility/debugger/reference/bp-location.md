---
description: 指定用來描述中斷點位置的結構類型。
title: BP_LOCATION |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 472dc7b2e642608691ea2adb2ad1a7dce170729f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144178"
---
# <a name="bp_location"></a>BP_LOCATION
指定用來描述中斷點位置的結構類型。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>成員
`bpLocationType`\
[BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)列舉中用來解讀聯 `bpLocation` 集或成員的值 `unionmemberX` 。

`bpLocation`.`bplocCodeFileLine`\
[僅限 c + +]如果為，則包含[BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)結構 `bpLocationType`  =  `BPLT_CODE_FILE_LINE` 。

`bpLocation.bplocCodeFuncOffset`\
[僅限 c + +]如果為，則包含[BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)結構 `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` 。

`bpLocation.bplocCodeContext`\
[僅限 c + +]如果為，則包含[BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)結構 `bpLocationType`  =  `BPLT_CODE_CONTEXT` 。

`bpLocation.bplocCodeString`\
[僅限 c + +]如果為，則包含[BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)結構 `bpLocationType`  =  `BPLT_CODE_STRING` 。

`bpLocation.bplocCodeAddress`\
[僅限 c + +]如果為，則包含[BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)結構 `bpLocationType`  =  `BPLT_CODE_ADDRESS` 。

`bpLocation.bplocDataString`\
[僅限 c + +]如果為，則包含[BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)結構 `bpLocationType`  =  `BPLT_DATA_STRING` 。

`bpLocation.bplocResolution`\
[僅限 c + +]如果為，則包含[BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)結構 `bpLocationType`  =  `BPLT_RESOLUTION` 。

`unionmember1`\
[僅限 c #]請參閱有關如何解讀的備註。

`unionmember2`\
[僅限 c #]請參閱有關如何解讀的備註。

`unionmember3`\
[僅限 c #]請參閱有關如何解讀的備註。

`unionmember4`\
[僅限 c #]請參閱有關如何解讀的備註。

## <a name="remarks"></a>備註
此結構是 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 結構的成員。

 [僅限 c #] `unionmemberX` 系統會根據下表來解讀成員。 向下查看值的左邊資料行， `bpLocationType` 然後查看其他資料行，以判斷每個 `unionmemberX` 成員代表的內容，並據以封送處理 `unionmemberX` 。 請參閱範例以瞭解如何在 c # 中解讀此結構的一部分。

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (內容) |[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (內容) |[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (內容) |`string` (條件運算式) |-|-|
|`BPLT_CODE_ADDRESS`|`string` (內容) |`string` (模組 URL) |`string` (函數名稱) |`string` (位址) |
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (內容) |`string` (日期運算式) |`uint` (的元素數目) |
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>範例
此範例示範如何 `BP_LOCATION` 在 c # 中針對型別解讀結構 `BPLT_DATA_STRING` 。 此特定類型顯示如何將 `unionmemberX` 所有可能格式的四個成員全部解讀 (物件、字串和數位) 。

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
