---
description: 比較物件與此物件。
title: IDebugObject：： IsEqual |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151658"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
比較物件與此物件。

## <a name="syntax"></a>語法

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>參數
`pObject`\
在代表要比較之物件的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件。

`pfIsEqual`\
擴展如果物件的值相等，則傳回非零 (`TRUE`) ; 否則傳回零 (`FALSE`) 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 一般來說，這個方法可以比較 `pObject` 參數和這個 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件所代表之值的位址; 如果位址相等，則可以將物件視為相等。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
