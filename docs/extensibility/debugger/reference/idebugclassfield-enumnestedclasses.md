---
title: IDebugClassField::枚外類 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734440"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
為嵌套在此類中的類創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回表示嵌套類清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有嵌套類,則返回 null 值。

## <a name="return-value"></a>傳回值
如果成功,則返回S_OK或返回S_FALSE如果沒有嵌套類。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
枚舉的每個元素都是描述嵌套類的[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件。

嵌套類是在另一個類中定義的類。 例如：

```
class RootClass {
   class NestedClass { }
};
```

[IEnum DebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)枚舉將包含一`NestedClass`個表示 類的物件。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
