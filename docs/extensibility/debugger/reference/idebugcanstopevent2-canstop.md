---
title: IDebugCanStopEvent2：： CanStop |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d3563fb46b9117ff7f142c5822c708deda34fda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880992"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
通知偵錯工具引擎 (DE) 是否要在目前的程式碼位置停止，或只是繼續執行。

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
在 `TRUE` 如果應該在目前的程式碼位置停止，則為非零 () ，否則為零 (`FALSE`) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個事件的接收者通常會呼叫 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 方法來判斷 DE 要停止的原因，然後 `IDebugCanStopEvent2::CanStop` 使用適當的回應來呼叫方法。

 如果停止，則會傳送描述停止原因的事件。 通常會傳送兩個事件、 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 介面所代表的使用者或信號中斷，以及由 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 介面表示的中斷點事件。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
