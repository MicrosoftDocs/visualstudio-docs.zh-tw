---
title: IDebugStackFrame3::攔截電流異常 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719488"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
當前堆疊幀上的調試器在要攔截當前異常時調用它。

## <a name="syntax"></a>語法

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>參數
`dwFlags`\
[在]指定不同的操作。 目前,僅支援[INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)INTERCEPT_EXCEPTION_ACTION`IEA_INTERCEPT`值 ,並且必須指定。

`pqwCookie`\
[出]標識特定異常的唯一值。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

 以下是最常見的錯誤返回。

|錯誤|描述|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|無法截獲當前異常。|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|當前執行幀尚未搜索處理程式。|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|此幀不支援此方法。|

## <a name="remarks"></a>備註
 引發異常時,調試器在異常處理過程中從關鍵點的運行時獲得控制。 在這些關鍵時刻,調試器可以詢問當前堆疊幀,如果幀想要攔截異常。 這樣,被截獲的異常實質上是堆疊幀的即時異常處理程式,即使該堆疊幀沒有異常處理程式(例如,程式代碼中的 try/catch 塊)。

 當調試器想知道是否應截獲異常時,它會在當前堆疊幀對象上調用此方法。 此方法負責處理異常的所有詳細資訊。 如果未實現[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)介面`InterceptStackException`,或者 該方法返回任何錯誤,則調試器將繼續正常處理異常。

> [!NOTE]
> 異常只能在託管代碼中截獲,也就是說,當正在調試的程式在 .NET 運行時運行時。 當然,如果第三方語言實現者願意,`InterceptStackException`可以在自己的調試引擎中實現。

 攔截完成後,發出[IDebug攔截異常完成事件2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)的信號。

## <a name="see-also"></a>另請參閱
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
