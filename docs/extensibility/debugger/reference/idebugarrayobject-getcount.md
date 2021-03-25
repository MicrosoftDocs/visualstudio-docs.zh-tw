---
description: 取得陣列中的元素計數。
title: IDebugArrayObject：： GetCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3a5d052fcb2c40f9dad76791aa992dbfbde72b0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058894"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
取得陣列中的元素計數。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>參數
`pdwElements`\
擴展傳回計數。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會將陣列物件的所有元素視為一維陣列，即使陣列物件為多維度也是一樣。 例如，假設有陣列 `myarray[3][2][6]` ，這個方法會傳回參數中的 36 `pdwElements` 。 您可以使用 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 方法，一次取出一個個別的元素。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
