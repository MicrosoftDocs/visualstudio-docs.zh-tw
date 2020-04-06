---
title: BP_LOCATION |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737938"
---
# <a name="bp_location"></a>BP_LOCATION
指定用於描述斷點位置的結構類型。

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
用於解釋`bpLocation`聯合`unionmemberX`或 成員[的BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)枚舉中的值。

`bpLocation`.`bplocCodeFileLine`\
[僅C++]如果包含[BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)BP_LOCATION_CODE_FILE_LINE`bpLocationType` = `BPLT_CODE_FILE_LINE`結構 。

`bpLocation.bplocCodeFuncOffset`\
[僅C++]如果[BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)包含`bpLocationType` = `BPLT_CODE_FUNC_OFFSET`BP_LOCATION_CODE_FUNC_OFFSET 結構 。

`bpLocation.bplocCodeContext`\
[僅C++]如果包含[BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)BP_LOCATION_CODE_CONTEXT`bpLocationType` = `BPLT_CODE_CONTEXT`結構 。

`bpLocation.bplocCodeString`\
[僅C++]如果[包含](../../../extensibility/debugger/reference/bp-location-code-string.md)BP_LOCATION_CODE_STRING`bpLocationType` = `BPLT_CODE_STRING`結構 。

`bpLocation.bplocCodeAddress`\
[僅C++]如果包含[BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)BP_LOCATION_CODE_ADDRESS`bpLocationType` = `BPLT_CODE_ADDRESS`結構 。

`bpLocation.bplocDataString`\
[僅C++]如果包含[BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)BP_LOCATION_DATA_STRING`bpLocationType` = `BPLT_DATA_STRING`結構 。

`bpLocation.bplocResolution`\
[僅C++]如果包含[BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)BP_LOCATION_RESOLUTION`bpLocationType` = `BPLT_RESOLUTION`結構 。

`unionmember1`\
[僅 C]請參閱有關如何解釋的備註。

`unionmember2`\
[僅 C]請參閱有關如何解釋的備註。

`unionmember3`\
[僅 C]請參閱有關如何解釋的備註。

`unionmember4`\
[僅 C]請參閱有關如何解釋的備註。

## <a name="remarks"></a>備註
此結構是[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的成員。

 [僅 C]成員`unionmemberX`根據下表進行解釋。 向下看值的左列,`bpLocationType`然後跨其他列查看以確定`unionmemberX`每個 成員表示的內容並相應地封`unionmemberX`送。 有關在 C# 中解釋此結構的一部分的方法,請參閱示例。

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(內容)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(內容)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(內容)|`string`(條件運算式)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(內容)|`string`(模組 URL)|`string`(功能名稱)|`string`(位址)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(內容)|`string`(資料運算式)|`uint`(元素)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>範例
此示例展示如何解釋`BP_LOCATION``BPLT_DATA_STRING`類型中的 C# 結構。 此特定類型展示如何以所有可能的格式(`unionmemberX`物件、字串和數位)解釋所有四個成員。

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

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

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
