---
description: IDebugProgram2：： Continue 會繼續從停止狀態執行此程式。 任何先前的執行狀態 (（例如步驟) ）都會保留，且程式會再次開始執行。
title: IDebugProgram2：： Continue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60f3cb4764a53d359e971020df8261d064c62e81
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076117"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
從停止狀態繼續執行此程式。 任何先前的執行狀態 (（例如步驟) ）都會保留，且程式會再次開始執行。

> [!NOTE]
> 此方法已被取代。 請改用 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 方法。

## <a name="syntax"></a>語法

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>參數
`pThread` 在代表執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 無論正在調試的程式有多少，或哪個程式產生停止事件，都會在這個程式上呼叫這個方法。 此實行必須保留先前的執行狀態 (例如步驟) 並繼續執行，如同在完成先前的執行之前從未停止執行。 也就是說，如果此程式中的執行緒正在進行一個執行中的作業，而且因為某些其他程式已停止，然後呼叫這個方法，則程式必須完成原始的逐步執行作業。

> [!WARNING]
> 在處理此呼叫時，請勿將停止事件或立即 (同步) 事件傳送到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ;否則，偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
