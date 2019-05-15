---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea1e70c40846b382364067eae473ec27777b5526
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615364"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
指定的中斷點解析位置的結構。

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
值，以從[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)列舉，指定如何解譯`bpResLocation`聯集或`unionmemberX`成員。

`bpResLocation.bpresCode`\
[C++只]包含[BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)結構，如果`bpType`  =  `BPT_CODE`。

`bpResLocation.bpresData`\
[C++只]包含[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)結構，如果`bpType`  =  `BPT_DATA`。

`bpResLocation.unused`\
[C++只]預留位置。

`unionmember1`\
[C#只]請參閱有關如何解譯的備註。

`unionmember2`\
[C#只]請參閱有關如何解譯的備註。

`unionmember3`\
[C#只]請參閱有關如何解譯的備註。

`unionmember4`\
[C#只]請參閱有關如何解譯的備註。

## <a name="remarks"></a>備註
此結構是隸屬[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)並[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構。

 [C#只]`unionmemberX`成員會根據下表來解譯。 往下的左側資料行`bpType`來判斷每個值然後跨`unionmemberX`成員表示和封送處理`unionmemberX`據此。 請參閱的方式來解譯此結構在 C# 中的範例。

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` （資料運算式）|`string` （函式名稱）|`string` （映像名稱）|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>範例
此範例示範如何解譯`BP_RESOLUTION_LOCATION`C# 中的結構。

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
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
