---
title: IDebugCanStopevent2::獲取原因 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734530"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
獲取調試引擎 (DE) 想要停止的原因。

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
[出]從描述此事件原因[的CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)枚舉中返回值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法通常在[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法之前調用,以便調用方可以確定是否將非`TRUE`零 (`IDebugCanStopEvent2::CanStop`) 傳遞給 方法。

 停止的原因可以是`CANSTOP_ENTRYPOINT`,這意味著 DE 已達到入口`CANSTOP_STEPIN`點,或者表示 DE 已踏入函數。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
