---
title: IDebugEngineProgram2：： Stop |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d7213dcd2484ba69caf51fdc21f52bba5bb3361
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506457"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
停止在此程式中執行的所有線程。

## <a name="syntax"></a>語法

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 當此程式在多程式環境中進行調試時，會呼叫這個方法。 當收到來自某個其他程式的停止事件時，就會在此程式上呼叫這個方法。 這個方法的實值應該是非同步;也就是說，在這個方法傳回之前，並非所有線程都必須停止。 此方法的實作為在此程式上呼叫[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)方法，可能會很簡單。

 當程式停止時，實施者應該傳送[IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) 。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
