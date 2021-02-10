---
title: IDebugThread2：： GetLogicalThread |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05d788f63d4807ccfd8e99d36cbf858df2be499f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940250"
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
