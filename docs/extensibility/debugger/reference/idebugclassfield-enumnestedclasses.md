---
title: IDebugClassField::EnumNestedClasses |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75b963f7a342a9ce2b276cc03ea5dece9316ff6d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313117"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
建立此類別中巢狀類別的列舉值。

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
[out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示巢狀類別的清單。 如果沒有巢狀的類別，則傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，會傳回 S_OK，或如果沒有巢狀的類別，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
列舉型別的每個項目是[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)描述巢狀的類別的物件。

巢狀的類別是定義在另一個類別的類別。 例如: 

```
class RootClass {
   class NestedClass { }
};
```

[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)列舉型別會包含一個物件，表示`NestedClass`類別。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
