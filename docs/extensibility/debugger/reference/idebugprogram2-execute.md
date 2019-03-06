---
title: IDebugProgram2::Execute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e1fc6ebaef7f514bf61251aec67554a18db4b0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698582"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
會繼續執行此程式從已停止的狀態。 在清除任何先前的執行狀態 （例如在步驟），並在程式啟動重新執行。

> [!NOTE]
>  這個方法已淘汰。 使用[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)方法改為。

## <a name="syntax"></a>語法

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當使用者從一些其他程式執行緒處於停止狀態，開始執行時，此方法稱為這個方案。 當使用者選取時，也會呼叫此方法**開始**命令**偵錯**在 IDE 中的功能表。 此方法的實作可能會非常簡單，像是呼叫[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)程式中目前的執行緒上的方法。

> [!WARNING]
>  不會傳送停止事件或即時 （同步） 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫; 否則為偵錯工具可能會停止回應。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)