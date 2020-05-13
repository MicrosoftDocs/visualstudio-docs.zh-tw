---
title: IDebugEngineProgram2::觀看運算式評估線程 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730370"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
允許(或不允許)在給定線程上進行表達式計算,即使程式已停止也是如此。

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
[在][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件,表示正在評估表達式的程式。

`dwTid`\
[在]指定線程的識別碼。

`dwEvalFlags`\
[在][EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉中的標誌組合,用於指定如何執行計算。

`pExprCallback`\
[在]用於發送運算式計算期間發生的調試事件的[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件。

`fWatch`\
[在]如果非零 (),`TRUE`允許在`dwTid`識別的 線程上進行表達式計算。否則,零`FALSE`() 不允許對該線程的表達式計算。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當會話調試管理器 (SDM)`pOriginatingProgram`要求 由參數標識的程序評估運算式時,它會透過調用此方法通知所有其他附加的程式。

 由於函數計算或任何`IDispatch`屬性的評估,一個程式中的運算式計算可能會導致代碼在另一個程式中運行。 因此,此方法允許表達式計算運行和完成,即使線程可能在此程式中停止。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
