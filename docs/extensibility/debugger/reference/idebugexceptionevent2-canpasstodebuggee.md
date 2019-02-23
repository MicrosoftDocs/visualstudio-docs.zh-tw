---
title: IDebugExceptionEvent2::CanPassToDebuggee |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93652efe19096466c853d758cc36aa022236068d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706440"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
決定偵錯引擎 (DE) 支援將此例外狀況傳遞至正在進行偵錯時繼續執行程式的選項。

## <a name="syntax"></a>語法

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>傳回值
 會傳回`S_OK`（例外狀況可以傳遞至程式） 或`S_FALSE`（無法傳遞的例外狀況）。

## <a name="remarks"></a>備註
 裝置必須傳送至偵錯工具的預設動作。 IDE 可能會收到[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件，並呼叫[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)方法，而不需呼叫`CanPassToDebuggee`方法。 因此，DE 應有上傳遞例外狀況，或不的預設案例。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)