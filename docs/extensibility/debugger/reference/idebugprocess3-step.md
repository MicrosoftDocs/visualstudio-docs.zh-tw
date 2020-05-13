---
title: IDebugProcess3::步驟 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723559"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
使進程步長為一個指令或語句。

> [!NOTE]
> 此方法應改為[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)。

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
[在][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件,表示要踩的線程。

`sk`\
[在][STEPKIND](../../../extensibility/debugger/reference/stepkind.md)值之一。

`step`\
[在][STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)值之一。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則返回錯誤代碼。

## <a name="remarks"></a>備註
 如果線程之間存在任何線程同步或通信,則當特定線程正在單步執行時,進程中的其他線程應運行。

 **警告**在處理此調用時,不要向[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件或立即(同步)事件;否則調試器可能會掛起。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
