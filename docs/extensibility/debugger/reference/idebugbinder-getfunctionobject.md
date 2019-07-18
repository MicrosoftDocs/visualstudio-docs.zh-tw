---
title: IDebugBinder::GetFunctionObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03078a09de94b886a659059192a5b67430cb5137
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337658"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
這個方法會取得[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用來建立函式參數的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>參數
`ppFunction`\
[out]傳回[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用來建立函式參數的介面。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)