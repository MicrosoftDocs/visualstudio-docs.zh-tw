---
title: IDebugProgram2：： Continue |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee73ea3a9b65635cf14d4d345bf22de4e9593989
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387079"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
從停止狀態繼續執行此程式。 任何先前的執行狀態（例如步驟）都會保留下來，而程式會再次開始執行。

> [!NOTE]
> 此方法已被取代。 請改用[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)方法。

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
`pThread`在代表執行緒的[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 這個方法會在這個程式上呼叫，不論正在調試多少程式，或是哪個程式產生了停止事件。 執行必須保留先前的執行狀態（例如步驟），並繼續執行，就好像在完成先前的執行之前從未停止過。 也就是說，如果此程式中的執行緒正在執行「逐步執行」作業，而且因為某個其他程式已停止而停止，然後呼叫此方法，則程式必須完成原始的「逐步執行」作業。

> [!WARNING]
> 在處理這個呼叫時，請勿傳送停止事件或立即（同步）事件給[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md);否則偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
