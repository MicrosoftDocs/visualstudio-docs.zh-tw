---
description: 取得陣列的元素。
title: IDebugArrayObject：： GetElement |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea10afac9f5503288d257833d6dd59f9ba56fc6f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158653"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
取得陣列的元素。

## <a name="syntax"></a>語法

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>參數
`dwIndex`\
在元素索引。

`ppElement`\
擴展傳回代表元素的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會將陣列物件的所有元素視為一維陣列，即使陣列物件為多維度也是一樣。 例如，假設陣列 `myarray[3][2][6]` 和 `dwIndex` 參數為20，這個方法會從傳回專案 `myarray[1][1][2]` ，而 `dwIndex` 21 的參數會從傳回元素 `myarray[1][1][3]` 。 您可以使用 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 方法來判斷陣列中的元素總數。

## <a name="see-also"></a>另請參閱
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
