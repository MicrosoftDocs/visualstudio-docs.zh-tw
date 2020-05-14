---
title: BP_RESOLUTION_LOCATION |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737818"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
指定斷點解析度位置的結構。

## <a name="syntax"></a>語法

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>成員
`bpType`\
[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)枚舉中指定如何`bpResLocation`解釋`unionmemberX`聯合或 成員的值。

`bpResLocation.bpresCode`\
[僅C++]如果[BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)包含`bpType` = `BPT_CODE`BP_RESOLUTION_CODE 結構 。

`bpResLocation.bpresData`\
[僅C++]如果[包含](../../../extensibility/debugger/reference/bp-resolution-data.md)BP_RESOLUTION_DATA`bpType` = `BPT_DATA`結構 。

`bpResLocation.unused`\
[僅C++]占位符。

`unionmember1`\
[僅 C]請參閱有關如何解釋的備註。

`unionmember2`\
[僅 C]請參閱有關如何解釋的備註。

`unionmember3`\
[僅 C]請參閱有關如何解釋的備註。

`unionmember4`\
[僅 C]請參閱有關如何解釋的備註。

## <a name="remarks"></a>備註
此結構是[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)和[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構的成員。

 [僅 C]成員`unionmemberX`根據下表進行解釋。 往下左欄的值,`bpType`然後跨,以確定`unionmemberX`每個 成員表示什麼,並相應地`unionmemberX`封送 。 有關在 C# 中解釋此結構的方法,請參閱示例。

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(資料運算式)|`string`(功能名稱)|`string`(影像名稱)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>範例
此示例演示如何在 C#`BP_RESOLUTION_LOCATION`中解釋結構。

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
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
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
