---
description: 調試引擎不會執行此方法。
title: IDebugThread2：： GetLogicalThread |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fe053a15ca6c89167b4b4cbf9bdffc8d7c334e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070969"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
調試引擎不會執行此方法。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>參數
`pStackFrame`\
在代表堆疊框架的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 物件。

`ppLogicalThread`\
擴展傳回 `IDebugLogicalThread2` 表示相關聯邏輯執行緒的介面。 調試引擎的執行應該將此值設定為 null 值。

## <a name="return-value"></a>傳回值
 調試引擎的實，一律會傳回 `E_NOTIMPL` 。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
