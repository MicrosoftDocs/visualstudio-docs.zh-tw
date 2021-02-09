---
title: IDebugFunctionObject：： CreateObjectNoConstructor |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2c47f51fb0ddc47218b11fe5673e0ede8362ff89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921092"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
建立沒有任何函式的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>參數
`pClassObject`\
在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件，代表要建立之物件的類型。

`ppObject`\
擴展傳回代表新建立之物件的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法來建立物件，該物件代表結構或複雜型別的實例， (不需要函式) ，也就是 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面所代表的函式的參數。

 如果物件參數需要函式，請呼叫 [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
