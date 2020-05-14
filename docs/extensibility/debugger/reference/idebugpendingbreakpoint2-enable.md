---
title: IDebug 待定突破點2::啟用 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f796aef9533e3861a870b0a0543ae6b4aeb11de1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725900"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
切換掛起斷點的啟用狀態。

## <a name="syntax"></a>語法

```cpp
HRESULT Enable(
    BOOL fEnable
);
```

```csharp
int Enable(
    int fEnable
);
```

## <a name="parameters"></a>參數
`fEnable`\
[在]設置為非零`TRUE`( ) 以啟用掛起的斷點,`FALSE`或設置為零 ( ) 以禁用。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_BP_DELETED`斷點已被刪除,則返回。

## <a name="remarks"></a>備註
啟用或禁用掛起的斷點時,從該斷點綁定的所有斷點都設置為相同的狀態。

即使斷點已啟用或禁用,也可以根據需要多次調用此方法。

## <a name="example"></a>範例
下面的示例演示如何為公開`CPendingBreakpoint`[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面的簡單對象實現此方法。

```cpp
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the bound breakpoint member variable is valid, then enable or
        // disable the bound breakpoint.
        if (m_pBoundBP)
        {
            m_pBoundBP->Enable(fEnable);
        }
        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to enabled or disabled depending on the passed BOOL condition.
        m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;
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
