---
description: 允許 (或不允許在指定的執行緒上執行) 運算式評估，即使程式已停止也一樣。
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94e049b4595c85e628b69a3613ae88ac27b013c7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153426"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
允許 (或不允許在指定的執行緒上執行) 運算式評估，即使程式已停止也一樣。

## <a name="syntax"></a>語法

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>參數
`pOriginatingProgram`\
在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件，代表正在評估運算式的程式。

`dwTid`\
在指定執行緒的識別碼。

`dwEvalFlags`\
在 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 列舉中的旗標組合，指定評估的執行方式。

`pExprCallback`\
在 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 物件，用來傳送運算式評估期間發生的偵錯工具事件。

`fWatch`\
在如果 () 非零 `TRUE` ，則允許在所識別的執行緒上進行運算式評估 `dwTid` ; 否則，零 (`FALSE`) 不允許在該執行緒上進行運算式評估。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當會話 debug manager (SDM) 要求以參數識別的程式時， `pOriginatingProgram` 會呼叫這個方法來通知所有其他附加的程式。

 某個程式中的運算式評估可能會導致程式碼在另一個程式中執行，因為任何屬性的函數評估或評估 `IDispatch` 。 因此，即使執行緒可能會在此程式中停止，這個方法也可讓運算式評估執行並完成。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
