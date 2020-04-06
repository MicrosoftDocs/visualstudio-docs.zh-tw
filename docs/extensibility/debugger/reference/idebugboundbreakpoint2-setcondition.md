---
title: IDebug邊界斷點2::設置條件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23fbe1b353378ca521fa802bdeae25fd12476df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735456"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
設置或更改與此綁定斷點關聯的條件。

## <a name="syntax"></a>語法

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>參數
`bpCondition`\
[在]描述條件[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)枚舉中的值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_BP_DELETED`綁定斷點物件的狀態設置`BPS_DELETED`為[(BP_STATE](../../../extensibility/debugger/reference/bp-state.md)枚舉的一部分),則返回。

## <a name="remarks"></a>備註
 以前與此斷點關聯的任何條件都將丟失。

## <a name="see-also"></a>另請參閱
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
