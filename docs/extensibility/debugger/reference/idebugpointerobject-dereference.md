---
title: IDebugPointer物件::De引用 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725572"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
獲取指向的物件。

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
[在]指向物件開頭的簡單位元組偏移。

`ppObject`\
[出]返回表示指向的物件的[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md),以及偏移(如果有)。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。 如果此物件不指向另一個物件,則返回E_FAIL。

## <a name="remarks"></a>備註
 指向的物件可以是基元類型或更複雜的類型,如類或結構。

## <a name="see-also"></a>另請參閱
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
