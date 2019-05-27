---
title: IDebugBreakpointUnboundEvent2::GetBreakpoint |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetBreakpoint
ms.assetid: ad73a207-b778-4dc5-b645-5ec668a63333
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a6dbb866e72dcdb0993b4739ba34b5fda29e403
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210010"
---
# <a name="idebugbreakpointunboundevent2getbreakpoint"></a>IDebugBreakpointUnboundEvent2::GetBreakpoint
取得中斷點變成未繫結。

## <a name="syntax"></a>語法

```cpp
HRESULT GetBreakpoint(
    IDebugBoundBreakpoint2** ppBP
);
```

```csharp
int GetBreakpoint(
    out IDebugBoundBreakpoint2 ppBP
);
```

## <a name="parameters"></a>參數
`ppBP`\
[out]傳回[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)表示變成未繫結的中斷點物件。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="example"></a>範例
下列範例示範如何實作這個方法，如**CBreakpointUnboundDebugEventBase**公開 （expose） 的物件[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)介面。

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetBreakpoint(
    IDebugBoundBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pbp )
        {
            IDebugBoundBreakpoint2 *pibp;

            hRes = m_pbp->QueryInterface(IID_IDebugBoundBreakpoint2, (void **) & pibp);

            if ( S_OK == hRes )
                *ppbp = pibp;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>另請參閱
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
