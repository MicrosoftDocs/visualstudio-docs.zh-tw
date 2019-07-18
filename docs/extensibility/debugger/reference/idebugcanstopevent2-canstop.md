---
title: IDebugCanStopEvent2::CanStop |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab59cf5d077c4e397373c4c86b864ed17749fc19
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351262"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
通知要停止在目前的程式碼位置，或只是繼續執行偵錯引擎 (DE)。

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
[in]非零 (`TRUE`) 如果 DE 應該停止的目前位置的程式碼; 否則為零 (`FALSE`)。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個事件的接收者通常會呼叫[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)方法，以判斷 DE 想要停止的原因，然後呼叫`IDebugCanStopEvent2::CanStop`具有適當的回應方法。

 如果 DE 停止時，它會傳送描述停止的原因的事件。 通常有兩個傳送的事件，由使用者或訊號中斷[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)介面，而且所代表的中斷點事件[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)