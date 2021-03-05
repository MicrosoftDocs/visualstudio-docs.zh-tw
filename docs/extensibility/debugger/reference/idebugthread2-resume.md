---
description: 繼續執行執行緒。
title: IDebugThread2：： Resume |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64a7d5509ac098f6b3a47c3606b6ec530bb6b65b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164496"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
繼續執行執行緒。

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
擴展傳回繼續作業之後的暫停計數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這種方法的每個呼叫都會遞減暫止計數，直到到達0為止，實際上繼續執行。 此暫止計數會顯示在 [ **執行緒** ] 偵錯工具視窗中。

 針對這個方法的每個呼叫，都必須有一個 [暫](../../../extensibility/debugger/reference/idebugthread2-suspend.md) 止方法的呼叫。 暫止計數會決定 `IDebugThread2::Suspend` 目前為止已呼叫方法的次數。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [暫止](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
