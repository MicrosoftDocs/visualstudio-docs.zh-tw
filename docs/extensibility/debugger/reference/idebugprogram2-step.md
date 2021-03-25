---
description: 執行步驟。
title: IDebugProgram2：： Step |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2470c62215c8c708056f7c123adc5eac3a5e389d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084489"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
執行步驟。

> [!NOTE]
> 此方法已被取代。 請改用 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) 方法。

## <a name="syntax"></a>語法

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>參數
`pThread`\
在代表正在逐步進行之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

`sk`\
在 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 列舉中的值，可指定步驟的種類。

`step`\
在 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 列舉中的值，可指定步驟 (的單位，例如，依語句或指令) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 如果執行緒之間有任何執行緒同步處理或通訊，則程式中的其他執行緒應在特定執行緒執行時執行。

> [!WARNING]
> 在處理此呼叫時，請勿將停止事件或立即 (同步) 事件傳送到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ;否則，偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
