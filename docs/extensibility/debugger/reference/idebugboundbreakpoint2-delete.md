---
description: 刪除中斷點。
title: IDebugBoundBreakpoint2：:D elete |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::Delete
helpviewer_keywords:
- Delete method
- IDebugBoundBreakpoint2::Delete method
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6dbe1877144813ab36c437f8163dc64fcdcc78d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088961"
---
# <a name="idebugboundbreakpoint2delete"></a>IDebugBoundBreakpoint2::Delete
刪除中斷點。

## <a name="syntax"></a>語法

```cpp
HRESULT Delete( 
    void 
);
```

```csharp
int Delete();
```

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 如果系結 `E_BP_DELETED` 中斷點物件的狀態設定為 `BPS_DELETED` [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 列舉) 的 (部分，則會傳回。

## <a name="example"></a>範例
下列範例顯示如何針對 `CBoundBreakpoint` 公開 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 介面的簡單物件，執行這個方法。

```
HRESULT CBoundBreakpoint::Delete(void)
{
    HRESULT hr;

    // Verify that the bound breakpoint has not been
    // deleted. If deleted, then return hr = E_BP_DELETED.
    if (m_state != BPS_DELETED)
    {
        m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);

        // Change the state of the breakpoint to BPS_DELETED.
        m_state = BPS_DELETED;
        hr = S_OK;
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
