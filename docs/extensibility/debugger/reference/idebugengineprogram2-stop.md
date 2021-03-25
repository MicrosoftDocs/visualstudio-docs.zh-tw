---
description: 停止在此程式中執行的所有線程。
title: IDebugEngineProgram2：： Stop |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7263756a0a8bacbbc6f90e327916cec8868d8f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077365"
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
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 當在多程式環境中進行此程式的偵錯工具時，會呼叫這個方法。 收到來自某個其他程式的停止事件時，會在此程式上呼叫這個方法。 此方法的實值應該是非同步;也就是說，並非所有線程都必須在此方法傳回之前停止。 此方法的實作為在此程式上呼叫 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 方法，可能會很簡單。

 實施者應該在程式停止時傳送 [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) 。

## <a name="see-also"></a>另請參閱
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
