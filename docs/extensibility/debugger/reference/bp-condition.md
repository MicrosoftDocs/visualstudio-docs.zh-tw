---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c37699e965698b4f5700bc1994ba25c8c0bbbd5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722313"
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
`pThread` [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示包含中斷點的應用程式的使用中執行緒。

`styleCondition` 值，以從[BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)列舉型別描述此中斷點條件的樣式。

`bstrContext` 中斷點的位置。

`bstrCondition` 引發中斷點的條件。

`nRadix` 用來評估數字的任何資訊的基數。

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
