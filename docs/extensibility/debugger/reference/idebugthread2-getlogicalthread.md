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
ms.openlocfilehash: 9e57d3deac01b00f1f332b34075d74f6402235f4
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224025"
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