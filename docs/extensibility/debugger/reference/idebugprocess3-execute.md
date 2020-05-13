---
title: IDebugProcess3::執行 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723677"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
繼續從已停止狀態運行此過程。 清除任何以前的執行狀態(如步驟),進程將再次開始執行。

> [!NOTE]
> 此方法應改為[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。

## <a name="syntax"></a>語法

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>參數
`pThread`\
[在]表示要執行的線程的[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當使用者從其他進程線程中的停止狀態開始執行時,此過程將調用此方法。 當使用者從 IDE 中的 **「調試」** 選單中選擇 **「開始」** 命令時,也會調用此方法。 此方法的實現可能非常簡單,例如在進程中的當前線程上調用[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)方法。

> [!WARNING]
> 在處理此調用時,不要向[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)發送停止事件或立即(同步)事件;否則調試器可能會掛起。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
