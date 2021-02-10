---
title: IDebugBoundBreakpoint2：： GetHitCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 875f1e55953d412e0c6dc49f1b00bd24cf589446
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945821"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
取得這個系結中斷點的目前計數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetHitCount( 
   DWORD* pdwHitCount
);
```

```csharp
int GetHitCount( 
   out uint pdwHitCount
);
```

## <a name="parameters"></a>參數
`pdwHitCount`\
擴展傳回計數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 如果系結 `E_BP_DELETED` 中斷點物件的狀態設定為 `BPS_DELETED` [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 列舉) 的 (部分，則會傳回。

## <a name="remarks"></a>備註
 計數是在目前的會話執行期間引發此中斷點的次數。

## <a name="see-also"></a>另請參閱
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
