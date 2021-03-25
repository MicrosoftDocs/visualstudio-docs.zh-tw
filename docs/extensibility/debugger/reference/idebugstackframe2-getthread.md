---
description: 取得與堆疊框架相關聯的執行緒。
title: IDebugStackFrame2：： GetThread |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetThread
helpviewer_keywords:
- IDebugStackFrame2::GetThread
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd720fbfd20e50a682b77cdeff09f9b8ff0708a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053279"
---
# <a name="idebugstackframe2getthread"></a>IDebugStackFrame2::GetThread
取得與堆疊框架相關聯的執行緒。

## <a name="syntax"></a>語法

```cpp
HRESULT GetThread ( 
   IDebugThread2** ppThread
);
```

```csharp
int GetThread ( 
   out IDebugThread2 ppThread
);
```

## <a name="parameters"></a>參數
`ppThread`\
擴展傳回代表執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
