---
description: 設定系結中斷點的計數。
title: IDebugBoundBreakpoint2：： SetHitCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63284fea43c283ad291e0207946fe6f5d36f5a4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095767"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
設定系結中斷點的計數。

## <a name="syntax"></a>語法

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>參數
`dwHitCount`\
在要設定的計數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 如果系結 `E_BP_DELETED` 中斷點物件的狀態設定為 `BPS_DELETED` [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 列舉) 的 (部分，則會傳回。

## <a name="remarks"></a>備註
 計數是在目前的會話執行期間引發此中斷點的次數。

 這個方法通常會由 debug 引擎呼叫，以更新此中斷點上的目前計數。

## <a name="see-also"></a>另請參閱
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
