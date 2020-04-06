---
title: IDebugexception2::PasstoDebuggee |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729828"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
指定是否應將異常傳遞到執行恢復時正在調試的程式,還是應丟棄該異常。

## <a name="syntax"></a>語法

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>參數
`fPass`\
[在]如果異常應在`TRUE`執行恢復時傳遞給正在調試的程式,則為非零 ( ), 如果應`FALSE`丟棄異常, 則為零 ()。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 調用此方法實際上不會導致在正在調試的程序中執行任何代碼。 調用只是為了為下一個代碼執行設置狀態。 例如,對[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)方法的調`S_OK`用可能會 隨[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)返回。`dwState` 欄位設定為`EXCEPTION_STOP_SECOND_CHANCE`。

 IDE 可能會接收[IDebugExceptionEvent2 事件](../../../extensibility/debugger/reference/idebugexceptionevent2.md)並呼叫["繼續"](../../../extensibility/debugger/reference/idebugprogram2-continue.md)方法。 如果不調用方法,調試引擎 (DE) 應具有處理該`PassToDebuggee`情況的 默認行為。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
