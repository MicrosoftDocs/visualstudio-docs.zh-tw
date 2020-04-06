---
title: IDebugProgram2::步驟 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722766"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
執行步驟。

> [!NOTE]
> 此方法已被取代。 改用[步驟](../../../extensibility/debugger/reference/idebugprocess3-step.md)方法。

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
[在]表示正在踩走的線程的[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

`sk`\
[在][STEPKIND](../../../extensibility/debugger/reference/stepkind.md)枚舉中指定步驟類型的值。

`step`\
[在][STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)枚舉中指定步進單位的值(例如,通過語句或指令)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果線程之間存在任何線程同步或通信,則當特定線程正在單步執行時,程式中的其他線程應運行。

> [!WARNING]
> 在處理此調用時,不要向[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件或立即(同步)事件;否則調試器可能會掛起。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
