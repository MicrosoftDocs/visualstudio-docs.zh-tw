---
title: IDebugProcess3：： Continue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ac7109b9f92a4ed7eecf57095c44fc4208b9f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891055"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
從停止狀態繼續執行此進程。 任何先前的執行狀態 (（例如步驟) ）都會保留，且進程會再次開始執行。

> [!NOTE]
> 應該使用這個方法，而不是 [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。

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
`pThread`\
在代表要繼續之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 無論正在進行的處理常式有多少個進程，或是哪一個進程產生停止事件，都會在這個進程上呼叫這個方法。 此實行必須保留先前的執行狀態 (例如步驟) 並繼續執行，如同在完成先前的執行之前從未停止執行。 也就是說，如果此進程中的執行緒正在進行一個執行中的作業，而且因為某些其他進程已停止，然後再 `Continue` 呼叫，則指定的執行緒必須完成原始的逐步執行作業。

 **警告** 在處理此呼叫時，請勿將停止事件或立即 (同步) 事件傳送到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ;否則，偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
