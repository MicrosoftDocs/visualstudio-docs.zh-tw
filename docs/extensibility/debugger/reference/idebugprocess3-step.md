---
description: 使進程逐步執行一個指令或語句。
title: IDebugProcess3：： Step |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85df970c073fa2203873733073c5b6b85cabe06
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150129"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
使進程逐步執行一個指令或語句。

> [!NOTE]
> 應該使用這個方法，而不是 [步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)。

## <a name="syntax"></a>語法

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>參數
`pThread`\
在代表正在逐步進行之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

`sk`\
在其中一個 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 值。

`step`\
在其中一個 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果執行緒之間有任何執行緒同步處理或通訊，則程式中的其他執行緒應該在特定執行緒執行時執行。

 **警告** 在處理此呼叫時，請勿將停止事件或立即 (同步) 事件傳送到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ;否則，偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
