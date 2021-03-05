---
description: 取得陣列中所有元素的列舉值。
title: IDebugArrayObject：： GetElements |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33840f3f5d5a65cf1ed929049f0b85801724a5c9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158549"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
取得陣列中所有元素的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
擴展傳回允許列舉所有元素的 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 或者，您也可以使用 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 和 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 方法來逐一查看元素。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
