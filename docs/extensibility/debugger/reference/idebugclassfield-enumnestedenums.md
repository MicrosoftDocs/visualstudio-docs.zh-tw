---
title: IDebugClassField::枚外數位 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734403"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
為此類的嵌套枚舉器創建枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回表示嵌套枚舉清單的[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件。 如果沒有嵌套枚舉,則返回 null 值。

## <a name="return-value"></a>傳回值
如果成功,則返回S_OK或返回S_FALSE如果沒有嵌套的枚舉器。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
枚舉的每個元素都是描述嵌套枚舉的[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)物件。

在類中聲明的枚舉被視為嵌套枚舉。 例如，假設：

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

該方法`EnumNestedEnums`將返回一個[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件,該物件包含一個表示枚舉`NestedEnum`的[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)物件。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
