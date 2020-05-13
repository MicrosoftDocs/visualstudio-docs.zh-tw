---
title: IDebugThread2:暫停 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718636"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
掛起線程。

## <a name="syntax"></a>語法

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>參數
`pdwSuspendCount`\
[出]在掛起操作后返回掛起計數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 對此方法的每個調用都會將掛起計數增加到 0 以上。 此掛起計數顯示在**線程**調試視窗中。

 對於對此方法的每個調用,以後必須調用[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)
