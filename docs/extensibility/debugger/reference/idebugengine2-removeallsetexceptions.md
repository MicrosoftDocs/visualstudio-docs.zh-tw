---
description: 移除 IDE 已針對特定執行時間架構或語言設定的例外狀況清單。
title: IDebugEngine2：： RemoveAllSetExceptions |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7832dd89ddfbdb15908934ff3ba36ab309d08fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153959"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
移除 IDE 已針對特定執行時間架構或語言設定的例外狀況清單。

## <a name="syntax"></a>語法

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>參數
`guidType`\
在適用于語言的 GUID 或針對執行時間架構所特有之 debug engine 的 GUID。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所移除的例外狀況是由先前對 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) 方法的呼叫所設定。

 若要移除特定的例外狀況，請呼叫 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
