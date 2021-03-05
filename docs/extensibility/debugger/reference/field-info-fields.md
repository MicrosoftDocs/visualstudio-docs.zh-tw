---
description: 指定要對 IDebugField 物件取得哪些資訊。
title: FIELD_INFO_FIELDS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 024c12d5112398e055141a8db4995f2801ca5401
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170285"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
指定要對 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件取得哪些資訊。

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
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
初始化/使用 `bstrFullName` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 結構中的欄位。

`FIF_NAME`\
初始化/使用 `bstrName` 結構中的欄位 `FIELD_INFO` 。

`FIF_TYPE`\
初始化/使用 `bstrType` 結構中的欄位 `FIELD_INFO` 。

`FIF_MODIFIERS`\
初始化/使用 `bstrModifiers` 結構中的欄位 `FIELD_INFO` 。

## <a name="remarks"></a>備註
這些值也會以引數的形式傳遞至 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法，以指定要初始化 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 結構的哪些欄位。

這些值也會用在結構的成員中， `dwFields` `FIELD_INFO` 以指出哪些欄位已使用且有效。

這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
