---
title: IDebugThread2:獲取邏輯線程 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718852"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
調試引擎不實現此方法。

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
[在]表示堆疊幀的[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)物件。

`ppLogicalThread`\
[出]返回表示`IDebugLogicalThread2`關聯邏輯線程的介面。 除錯引擎實現應將此值設定為 null 值。

## <a name="return-value"></a>傳回值
 除錯引擎可傳回`E_NOTIMPL`。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
