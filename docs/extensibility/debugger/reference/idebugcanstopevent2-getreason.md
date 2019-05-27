---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1bfc8b813f1016f3c040d47120675f881b92020
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203145"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
取得偵錯引擎 (DE) 為何想要停止的原因。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>參數
`pcr`\
[out]傳回值，以從[CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)列舉，描述這個事件的原因。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法通常會呼叫之前[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法，讓呼叫者可以判斷是否要傳遞非零 (`TRUE`) 來`IDebugCanStopEvent2::CanStop`方法。

 正在停止的原因可以是`CANSTOP_ENTRYPOINT`，這表示裝置已達到進入點，或`CANSTOP_STEPIN`，這表示 DE 已逐步執行函式。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)