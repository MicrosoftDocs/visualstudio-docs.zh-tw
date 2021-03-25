---
description: 使用函式建立物件。
title: IDebugFunctionObject：： CreateObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27608634859ae96a8fb9461076397bb6df53570d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073556"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
使用函式建立物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>參數
`pConstructor`\
在 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 物件，代表要建立之物件的函式。

`dwArgs`\
在陣列中的參數數目 `pArg` 。 代表傳遞至函式的參數數目。

`pArg`\
在 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件的陣列，代表傳遞至該函式的參數。

`ppObject`\
擴展傳回， `IDebugObject` 表示新建立的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法來建立物件，該物件代表類別 (的實例，或其他) 需要函式的複雜型別，而該函式是函式的參數，該函式是 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面所代表的函式的參數。

 如果物件參數不需要函式，請呼叫 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
