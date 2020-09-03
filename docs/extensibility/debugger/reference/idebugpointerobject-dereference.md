---
title: IDebugPointerObject：:D ereference 書庫 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725572"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
取得指向的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>參數
`dwIndex`\
在從指向之物件的開頭算起的簡單位元組位移。

`ppObject`\
擴展傳回代表所指向之物件的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件，加上 offset （如果有的話）。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。 如果這個物件沒有指向另一個物件，則會傳回 E_FAIL。

## <a name="remarks"></a>備註
 指向的物件可以是基本或更複雜的類型，例如類別或結構。

## <a name="see-also"></a>另請參閱
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
