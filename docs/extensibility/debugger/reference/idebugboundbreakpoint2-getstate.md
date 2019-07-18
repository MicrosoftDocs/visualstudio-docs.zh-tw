---
title: IDebugBoundBreakpoint2::GetState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugBoundBreakpoint2::GetState method
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d930b1a68b97548c02edd35fa48ef8f3a1935181
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314480"
---
# <a name="idebugboundbreakpoint2getstate"></a>IDebugBoundBreakpoint2::GetState
取得這個繫結中斷點的狀態。

## <a name="syntax"></a>語法

```cpp
HRESULT GetState( 
    BP_STATE* pState
);
```

```csharp
int GetState( 
    out enum_BP_STATE pState
);
```

## <a name="parameters"></a>參數
`pState`\
[out]傳回值，以從[BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉，描述中斷點的狀態。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何實作這個方法來簡單`CBoundBreakpoint`公開的物件[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。

```
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)
{
    HRESULT hr;

    // Check for a valid pointer to pState and assign the local state variable.
    if (pState)
    {
        *pState = m_state;
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
