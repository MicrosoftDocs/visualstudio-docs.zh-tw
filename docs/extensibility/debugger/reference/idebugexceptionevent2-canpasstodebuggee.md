---
description: 決定 debug engine (DE) 是否支援將這個例外狀況傳遞至執行繼續時所要進行偵錯工具的選項。
title: IDebugExceptionEvent2：： CanPassToDebuggee |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152880"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
決定 debug engine (DE) 是否支援將這個例外狀況傳遞至執行繼續時所要進行偵錯工具的選項。

## <a name="syntax"></a>語法

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>傳回值
 `S_OK`傳回 (例外狀況可以傳遞給程式) 或 `S_FALSE` (例外狀況無法在) 傳遞。

## <a name="remarks"></a>備註
 DE 必須有傳遞至偵錯工具的預設動作。 IDE 可能會接收 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 事件並呼叫 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 方法，而不需要呼叫 `CanPassToDebuggee` 方法。 因此，DE 應該要有一個預設案例，才能在上傳遞例外狀況。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
