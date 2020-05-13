---
title: IDebugBound斷點2::Delete |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::Delete
helpviewer_keywords:
- Delete method
- IDebugBoundBreakpoint2::Delete method
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a480a97c14b568565fee9b1b82d672db11f4ebab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735651"
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
如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_BP_DELETED`綁定斷點物件的狀態設置`BPS_DELETED`為[(BP_STATE](../../../extensibility/debugger/reference/bp-state.md)枚舉的一部分),則返回。

## <a name="example"></a>範例
下面的示例演示如何為公開`CBoundBreakpoint`[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面的簡單對象實現此方法。

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
