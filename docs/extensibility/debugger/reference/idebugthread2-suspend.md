---
description: 暫停執行緒。
title: IDebugThread2：：暫止 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f80799961ccce4b3492b46801b1917055742666
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164444"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
暫停執行緒。

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
擴展傳回暫止作業之後的暫停計數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 每次呼叫此方法時，都會將暫止計數遞增0。 此暫止計數會顯示在 [ **執行緒** ] 偵錯工具視窗中。

 每次呼叫此方法時，都必須稍後再呼叫 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)
