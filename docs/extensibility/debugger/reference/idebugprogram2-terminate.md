---
title: IDebugProgram2：： Terminate |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a186bd39dab7ab1f7228504070f50b3aa6c311
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911897"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
終止程式。

## <a name="syntax"></a>語法

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 可能的話，程式將會終止並從進程中卸載;否則，debug engine (DE) 將會執行任何必要的清除。

 IDE 會呼叫這個方法或 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) 方法，通常是為了回應使用者停止所有的偵錯工具。 在理想的情況下，此方法的執行應該在進程內終止程式。 如果無法這麼做，則應該避免程式在此程式中執行其他作業 (並執行任何必要的清除) 。 如果此 `IDebugProcess2::Terminate` 方法是由 IDE 所呼叫，則在呼叫方法之後，將會終止整個進程 `IDebugProgram2::Terminate` 。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
