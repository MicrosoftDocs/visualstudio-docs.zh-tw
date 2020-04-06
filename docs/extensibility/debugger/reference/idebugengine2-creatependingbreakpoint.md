---
title: IDebugEngine2::創建待處理斷點 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731126"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
在除錯引擎 (DE) 中建立掛起的斷點。

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
[在]描述要創建的掛起斷點的[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)物件。

`ppPendingBP`\
[出]返回表示掛起斷[點的 IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)物件。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_FAIL``pBPRequest`參數與 DE 支援的任何語言`pBPRequest`不匹配, 則通常傳回該參數無效或不完整。

## <a name="remarks"></a>備註
掛起的斷點實質上是綁定斷點到代碼所需的所有資訊的集合。 在調用[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)方法之前,從此方法返回的掛起斷點不會綁定到代碼。

對於用戶設置的每個掛起的斷點,會話調試管理器 (SDM) 在每個附加的 DE 中調用此方法。 由 DE 驗證斷點是否對運行在該 DE 中的程式有效。

當使用者在代碼行上設置斷點時,DE 可以自由地將斷點綁定到文檔中對應於此代碼的最近行。 這樣,使用者就可以在多行語句的第一行上設置斷點,但將其綁定到最後一行(其中所有代碼都歸於調試資訊中)。

## <a name="example"></a>範例
下面的示例演示如何實現此方法的簡單`CProgram`物件。 然後,DE 的`IDebugEngine2::CreatePendingBreakpoint`實現可以將所有調用轉發到每個程式中的方法的此實現。

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
