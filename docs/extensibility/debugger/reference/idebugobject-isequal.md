---
title: IDebugObject::是平等的 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726511"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
將物件與此對象進行比較。

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
[在]表示要與之比較的物件的[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)。

`pfIsEqual`\
[出]如果物件的值相等,`TRUE`則傳回非零 ( ),否則,返回零`FALSE`()。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 通常,此方法可以比較`pObject`參數和此[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件表示的值的位址;如果位址相等,則物件可以視為相等。

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
