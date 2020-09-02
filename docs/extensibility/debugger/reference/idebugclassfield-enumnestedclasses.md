---
title: IDebugClassField：： EnumNestedClasses |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734440"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
建立在這個類別中嵌套之類別的列舉值。

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
擴展傳回代表嵌套類別清單的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件。 如果沒有任何嵌套類別，則會傳回 null 值。

## <a name="return-value"></a>傳回值
如果成功，會傳回 S_OK，如果沒有任何嵌套類別，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
列舉的每個元素都是描述嵌套類別的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件。

嵌套類別是在另一個類別內定義的類別。 例如：

```
class RootClass {
   class NestedClass { }
};
```

[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)列舉會包含代表類別的一個物件 `NestedClass` 。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
