---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20db594fcc00f641634bfaae8d5342d4b520d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337430"
---
# <a name="bpcondition"></a>BP_CONDITION
描述用以引發中斷點的條件。

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
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示包含中斷點的應用程式的使用中執行緒。

`styleCondition`\
值，以從[BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)列舉型別描述此中斷點條件的樣式。

`bstrContext`\
中斷點的位置。

`bstrCondition`\
引發中斷點的條件。

`nRadix`\
用來評估數字的任何資訊的基數。

## <a name="remarks"></a>備註
此結構是隸屬[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)並[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。

此結構也會做為參數傳遞[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)並[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)方法。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
