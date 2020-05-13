---
title: IDebugThread2:恢復 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718682"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
恢復線程的執行。

## <a name="syntax"></a>語法

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>參數
`pdwSuspendCount`\
[出]返回恢復操作后的掛起計數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 對此方法的每個調用都會取消掛起計數,直到它達到 0,此時實際恢復執行。 此掛起計數顯示在**線程**調試視窗中。

 對於對此方法的每個調用,必須對[掛起](../../../extensibility/debugger/reference/idebugthread2-suspend.md)方法進行以前的調用。 掛起計數確定到目前為止調用`IDebugThread2::Suspend`該方法的次數。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [暫停](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
