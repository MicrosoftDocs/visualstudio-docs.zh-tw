---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4273d1c8bff6f07fdcf12b5b324d8d42eb08799
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199728"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
偵錯引擎不會實作這個方法。

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
[in][IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件，代表堆疊框架。

`ppLogicalThread`\
[out]傳回`IDebugLogicalThread2`介面，表示相關聯的邏輯執行緒。 偵錯引擎實作應該將此設定為 null 值。

## <a name="return-value"></a>傳回值
 偵錯引擎實作永遠會傳回`E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)