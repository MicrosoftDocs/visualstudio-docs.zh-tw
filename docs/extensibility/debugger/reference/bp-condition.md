---
title: BP_CONDITION |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738099"
---
# <a name="bp_condition"></a>BP_CONDITION
描述斷點觸發的條件。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>成員
`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件,表示包含斷點的應用程式的活動線程。

`styleCondition`\
描述此斷點條件樣式[的BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)枚舉中的值。

`bstrContext`\
斷點的位置。

`bstrCondition`\
斷點的觸發條件。

`nRadix`\
用於評估任何數值資訊的 Radix。

## <a name="remarks"></a>備註
此結構是[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的成員。

此結構也作為參數傳遞給[Set 條件和](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)Set[條件](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)方法。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
