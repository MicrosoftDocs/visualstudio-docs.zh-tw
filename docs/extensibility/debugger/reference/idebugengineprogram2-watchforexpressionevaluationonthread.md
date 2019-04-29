---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c0572bfa8ebe1b70548483b17c58d08c8a0f9ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920378"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
允許 （或不允許） 發生在指定的執行緒上，即使該程式已停止的運算式評估。

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

#### <a name="parameters"></a>參數
 `pOriginatingProgram`

 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示已評估運算式的程式。

 `dwTid`

 [in]指定執行緒的識別碼。

 `dwEvalFlags`

 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉，指定要如何進行評估。

 `pExprCallback`

 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)用來傳送在運算式評估期間發生的偵錯事件的物件。

 `fWatch`

 [in]如果不是零 (`TRUE`)，讓運算式評估所識別的執行緒上`dwTid`; 否則為零 (`FALSE`) 不允許在該執行緒上的運算式評估。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 工作階段的偵錯管理員 (SDM) 的程式，其所識別的要求時`pOriginatingProgram`參數，來評估運算式，它會通知所有其他附加的程式，藉由呼叫這個方法。

 一個程式中的運算式評估可能會導致執行位於另一個，因為函式評估或評估的任何程式碼`IDispatch`屬性。 因為這個緣故，這個方法可讓執行並完成即使執行緒可能會停止此程式中的運算式評估。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)