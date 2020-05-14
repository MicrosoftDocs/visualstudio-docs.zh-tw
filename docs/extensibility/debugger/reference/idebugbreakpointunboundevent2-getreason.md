---
title: IDebugBreakpoint 無綁定事件2::獲取原因 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9830309f0a40aee37982554e8920a95d289eb74c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734715"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
獲取斷點未綁定的原因。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason
);
```

```csharp
int GetReason(
    out enum_ BP_UNBOUND_REASON pdwUnboundReason
);
```

## <a name="parameters"></a>參數
`pdwUnboundReason`\
[出]從[BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)枚舉返回值,指定斷點未綁定的原因。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
原因包括斷點在編輯和繼續操作後反彈到其他位置,或者確定斷點被錯誤地綁定。

## <a name="example"></a>範例
下面的示例演示如何為公開[IDebugBreakpoint UnbundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)介面的**CBreakpoint 未綁定 DebugEventBase**物件實現此方法。

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason)
{
    HRESULT hRes = E_FAIL;

    if ( EVAL(pdwUnboundReason) )
    {
        *pdwUnboundReason = m_dwReason;

        hRes = S_OK;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>另請參閱
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
