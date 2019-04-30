---
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f9afe4bb5087c7589415a6ae7fc143f5fd01b21
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413209"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
會繼續執行此程序，從停止的狀態。 在清除任何先前的執行狀態 （例如在步驟），並在處理序啟動重新執行。

> [!NOTE]
> 應該使用這個方法，而不是[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。

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

#### <a name="parameters"></a>參數
 `pThread`

 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示要執行的執行緒。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 當使用者從某些其他處理序的執行緒處於停止狀態，開始執行時，對此程序會呼叫這個方法。 當使用者選取時，也會呼叫此方法**開始**命令**偵錯**在 IDE 中的功能表。 此方法的實作可能會非常簡單，像是呼叫[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)程序中目前的執行緒上的方法。

> [!WARNING]
> 不會傳送停止事件或即時 （同步） 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫; 否則為偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)