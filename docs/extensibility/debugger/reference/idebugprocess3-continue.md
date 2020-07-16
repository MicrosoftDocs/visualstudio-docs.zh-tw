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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aba0863ad7c50bf5c14e7a30c06097825b8cf5ec
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386793"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
從停止狀態繼續執行此進程。 任何先前的執行狀態（例如步驟）都會保留下來，而且進程會再次開始執行。

> [!NOTE]
> 應該使用這個方法，而不是[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。

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
在代表要繼續之執行緒的[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 這個方法會在這個進程上呼叫，不論正在調試多少進程，或是哪個進程產生了停止事件。 執行必須保留先前的執行狀態（例如步驟），並繼續執行，就好像在完成先前的執行之前從未停止過。 也就是說，如果此處理程式中的執行緒正在執行「逐步執行」作業，而且因為某個其他進程停止而停止，然後 `Continue` 呼叫，則指定的執行緒必須完成原始的「逐步執行」作業。

 **警告**在處理這個呼叫時，請勿傳送停止事件或立即（同步）事件給[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md);否則偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
