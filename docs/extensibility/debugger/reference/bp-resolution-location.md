---
description: 指定中斷點解析位置的結構。
title: BP_RESOLUTION_LOCATION |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aefbb27a7eb693ceef3bd64afb610607697ac23e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089117"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
指定中斷點解析位置的結構。

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
[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列舉中的值，這個值會指定如何解讀聯 `bpResLocation` 集或 `unionmemberX` 成員。

`bpResLocation.bpresCode`\
[僅限 c + +]如果為，則包含[BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)結構 `bpType`  =  `BPT_CODE` 。

`bpResLocation.bpresData`\
[僅限 c + +]如果為，則包含[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)結構 `bpType`  =  `BPT_DATA` 。

`bpResLocation.unused`\
[僅限 c + +]預留位置。

`unionmember1`\
[僅限 c #]請參閱有關如何解讀的備註。

`unionmember2`\
[僅限 c #]請參閱有關如何解讀的備註。

`unionmember3`\
[僅限 c #]請參閱有關如何解讀的備註。

`unionmember4`\
[僅限 c #]請參閱有關如何解讀的備註。

## <a name="remarks"></a>備註
此結構是 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 和 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 結構的成員。

 [僅限 c #] `unionmemberX` 系統會根據下表來解讀成員。 向下查看值的左側資料行， `bpType` 然後以判斷每個 `unionmemberX` 成員代表的內容，並據以封送處理 `unionmemberX` 。 請參閱範例以瞭解如何在 c # 中解讀此結構。

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (日期運算式) |`string` (函數名稱) |`string` (映射名稱) |`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>範例
此範例示範如何 `BP_RESOLUTION_LOCATION` 在 c # 中解讀結構。

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

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
