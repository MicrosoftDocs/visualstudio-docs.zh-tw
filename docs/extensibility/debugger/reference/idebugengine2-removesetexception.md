---
description: 移除指定的例外狀況，使它不再由 debug 引擎處理。
title: IDebugEngine2：： RemoveSetException |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 588037ef9dcf495f8fbbb210acc3154c31558a32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153945"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
移除指定的例外狀況，使它不再由 debug 引擎處理。

## <a name="syntax"></a>語法

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>參數
`pException`\
在描述要移除之例外狀況的 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 先前呼叫 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 方法之前，必須先設定要移除的例外狀況。

 若要一次移除所有設定的例外狀況，請呼叫 [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
