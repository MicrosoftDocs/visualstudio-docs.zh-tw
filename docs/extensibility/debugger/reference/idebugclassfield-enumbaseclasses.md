---
title: IDebugClassfield:枚舉基礎類 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12317c549050be31ac9e19bc7b3d8a6683f743d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734468"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
為此類的基類創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\

[出]返回表示基類清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有基類,則返回 null 值。

## <a name="return-value"></a>傳回值
 如果成功,則返回S_OK,如果沒有基類S_SH_NO_BASE_CLASSES返回(並且`ppEnum`參數設置為空值);否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 枚舉器物件中的基類按最遠端基類最直接(或最派生)基類的順序指定。 例如,給定C++類:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 枚舉將返回按順序`Level2`返回基類。 `Root` `Level1`

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
