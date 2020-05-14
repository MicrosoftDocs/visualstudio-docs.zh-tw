---
title: IDebugEvent回撥2::事件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729903"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
發送調試事件通知。

## <a name="syntax"></a>語法

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>參數
`pEngine`\
[在]表示發送此事件的調試引擎 (DE) 的[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)物件。 需要 DE 來填寫此參數。

`pProcess`\
[在][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件,表示事件發生的進程。 此參數由會話調試管理器 (SDM) 填充。 DE 始終傳遞此參數的 null 值。

`pProgram`\
[在][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示發生此事件的程式。 對於大多數事件,此參數不是 null 值。

`pThread`\
[在][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件,表示發生此事件的線程。 對於停止事件,此參數不能為空值,因為堆疊幀是從此參數獲取的。

`pEvent`\
[在]表示調試事件的[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)物件。

`riidEvent`\
[在]GUID,用於標識要從`pEvent`參數獲取的事件介面。

`dwAttrib`\
[在][事件屬性](../../../extensibility/debugger/reference/eventattributes.md)枚舉中標誌的組合。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 呼叫此方法時,`dwAttrib`參數必須與從[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)方法傳回的值`pEvent`匹配,因為在 參數中傳遞的事件物件上調用了該值。

 所有調試事件都是異步發佈的,無論事件本身是否是異步的。 當 DE 調用此方法時,返回值不指示事件是否已處理,僅指示是否接收了事件。 事實上,在大多數情況下,當此方法返回時,事件尚未處理。

## <a name="see-also"></a>另請參閱
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
