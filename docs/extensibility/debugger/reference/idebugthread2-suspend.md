---
title: IDebugThread2::Suspend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e45cee0acab5fb2b5165e28895ab9a7dcb3ed9c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915467"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
暫止的執行緒。

## <a name="syntax"></a>語法

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

#### <a name="parameters"></a>參數
 `pdwSuspendCount`

 [out]擱置作業之後，傳回的暫停計數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 每次呼叫此方法會遞增暫停計數大於 0。 此暫停計數會顯示在**執行緒**偵錯視窗。

 每次呼叫這個方法，必須稍後呼叫[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)