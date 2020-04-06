---
title: IDebugcanStopevent2:::可以停止 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734586"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
通知除錯引擎 (DE) 是否停止在目前的程式碼位置或只是繼續執行。

## <a name="syntax"></a>語法

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>參數
`fCanStop`\
[在]如果`TRUE`DE 應停止在目前的代碼位置,則非零 ( ) ;否則,零`FALSE`()。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此事件的接收方通常調用[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)方法以確定 DE 想要停止的原因,然後使用適當`IDebugCanStopEvent2::CanStop`的回應調用 該方法。

 如果 DE 停止,它將發送描述停止原因的事件。 通常發送兩個事件,一個由[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)介面表示的使用者或信號中斷,以及[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面表示的斷點事件。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
