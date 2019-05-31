---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01853df78bfe731ea4b7159f7b3ebe352f3c5eaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337676"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
指定要擷取其相關資訊[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

## <a name="syntax"></a>語法

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>欄位
`FIF_FULLNAME`\
初始化/使用`bstrFullName`欄位中[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)結構。

`FIF_NAME`\
初始化/使用`bstrName`欄位中`FIELD_INFO`結構。

`FIF_TYPE`\
初始化/使用`bstrType`欄位中`FIELD_INFO`結構。

`FIF_MODIFIERS`\
初始化/使用`bstrModifiers`欄位中`FIELD_INFO`結構。

## <a name="remarks"></a>備註
這些值也會傳遞做為引數[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)方法，以指定的哪些欄位[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)結構會進行初始化。

這些值也會在`dwFields`隸屬`FIELD_INFO`表示哪些欄位已使用且有效的結構。

這些旗標可能會結合的位元`OR`。

## <a name="requirements"></a>需求
標頭： sh.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
