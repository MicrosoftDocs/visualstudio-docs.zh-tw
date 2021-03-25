---
description: 在 debug engine 中建立暫止中斷點 (DE) 。
title: IDebugEngine2：： CreatePendingBreakpoint |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa06a4c88afecfebbd0b1258d7f1830dfdaad5ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093869"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
在 debug engine 中建立暫止中斷點 (DE) 。

## <a name="syntax"></a>語法

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>參數
`pBPRequest`\
在描述要建立之暫止中斷點的 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 物件。

`ppPendingBP`\
擴展傳回代表暫止中斷點的 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 物件。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 當參數 `E_FAIL` `pBPRequest` `pBPRequest` 無效或不完整時，如果參數不符合任何由 DE 所支援的語言，通常會傳回。

## <a name="remarks"></a>備註
暫止中斷點基本上是將中斷點系結至程式碼所需之所有資訊的集合。 在呼叫 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 方法之前，這個方法所傳回的暫止中斷點未系結至程式碼。

針對使用者所設定的每個暫止中斷點，會話 debug manager (SDM) 在每個附加的 DE 中呼叫這個方法。 它是由 DE 來確認中斷點是否適用于在該解除的程式中執行的程式。

當使用者在程式程式碼上設定中斷點時，可以自由地將中斷點系結至檔中與此程式碼對應的最接近行。 如此一來，使用者就可以在多行語句的第一行設定中斷點，但是將它系結到最後一行 (在) 的 debug 資訊中，所有程式碼都是以屬性化。

## <a name="example"></a>範例
下列範例顯示如何針對簡單的物件來執行此方法 `CProgram` 。 的 DE 的實， `IDebugEngine2::CreatePendingBreakpoint` 接著就可以在每個程式中，將所有對方法執行的呼叫轉送到。

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
