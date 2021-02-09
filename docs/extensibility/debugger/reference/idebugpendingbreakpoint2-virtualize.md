---
title: IDebugPendingBreakpoint2：：虛擬化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 242caf91b8f25f8bea6ff9c17820ed84c5fc98f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869670"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
切換此暫止中斷點的虛擬化狀態。 當暫止的中斷點已虛擬化時，每當新的程式碼載入程式時，debug engine 都會嘗試系結它。

## <a name="syntax"></a>語法

```cpp
HRESULT Virtualize(
    BOOL fVirtualize
);
```

```cpp
int Virtualize(
    int fVirtualize
);
```

## <a name="parameters"></a>參數
`fVirtualize`\
在設定為非零 (`TRUE`) 以虛擬化暫止中斷點，或設定為零 (`FALSE`) 以關閉虛擬化。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_BP_DELETED`如果中斷點已刪除，則會傳回。

## <a name="remarks"></a>備註
每次載入程式碼時，都會系結虛擬化的中斷點。

## <a name="example"></a>範例
下列範例顯示如何針對 `CPendingBreakpoint` 公開 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 介面的簡單物件，執行這個方法。

```cpp
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        if (fVirtualize)
        {
            // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            SetFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
        else
        {
            // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
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
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
