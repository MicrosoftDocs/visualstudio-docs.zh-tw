---
title: IDebugBound突破點2::獲取HitCount |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c821470cc81c1f4c495f6d71565d79cc9745f65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735512"
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
獲取此綁定斷點的當前命中計數。

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
[出]返回命中計數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_BP_DELETED`綁定斷點物件的狀態設置`BPS_DELETED`為[(BP_STATE](../../../extensibility/debugger/reference/bp-state.md)枚舉的一部分),則返回。

## <a name="remarks"></a>備註
 命中計數是此斷點在當前會話運行期間觸發的次數。

## <a name="see-also"></a>另請參閱
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
