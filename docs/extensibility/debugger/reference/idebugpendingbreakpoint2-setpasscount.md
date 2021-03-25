---
description: 設定或變更與暫止中斷點相關聯的傳遞計數。
title: IDebugPendingBreakpoint2：： SetPassCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d83249667bd9489b052f35a4d3d3b7ca826d540f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058348"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
設定或變更與暫止中斷點相關聯的傳遞計數。

## <a name="syntax"></a>語法

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>參數
`bpPassCount`\
在包含傳遞計數的 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_BP_DELETED`如果中斷點已刪除，則會傳回。

## <a name="remarks"></a>備註
 任何先前與暫止中斷點相關聯的傳遞計數都會遺失。 系統會呼叫從此暫止中斷點系結的所有中斷點，以將其傳遞計數設定為 `bpPassCount` 參數。

## <a name="see-also"></a>另請參閱
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
