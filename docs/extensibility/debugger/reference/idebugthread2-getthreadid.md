---
description: 取得系統執行緒識別碼。
title: IDebugThread2：： GetThreadId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39702dad7ad154e2922f217f36c13a47588cb06d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053031"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
取得系統執行緒識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>參數
`pdwThreadId`\
擴展傳回系統執行緒識別碼。

## <a name="return-value"></a>傳回值
如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
執行緒識別碼是用來識別進程中所有其他執行緒之間的執行緒。

## <a name="example"></a>範例
下列範例示範如何針對實 IDebugThread2 介面的簡單物件，執行這個方法 `CProgram` 。 [](../../../extensibility/debugger/reference/idebugthread2.md)

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
