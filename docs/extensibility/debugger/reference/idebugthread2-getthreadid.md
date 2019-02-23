---
title: IDebugThread2::GetThreadId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85dd439729763b594076e4fab076a213c10f5a46
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702079"
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

#### <a name="parameters"></a>參數
`pdwThreadId`

 [out]傳回系統執行緒識別碼。

## <a name="return-value"></a>傳回值
如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
執行緒識別碼用來識別處理序中的所有其他執行緒之間的執行緒。

## <a name="example"></a>範例
下列範例示範如何實作這個方法來簡單`CProgram`實作的物件[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)介面。

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
