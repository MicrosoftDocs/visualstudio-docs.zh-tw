---
title: FIELD_INFO_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736903"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
指定要檢索的關於[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件的資訊。

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
初始化/使用`bstrFullName`[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)結構中的欄位。

`FIF_NAME`\
初始化/使用結構`bstrName``FIELD_INFO`中的 欄位。

`FIF_TYPE`\
初始化/使用結構`bstrType``FIELD_INFO`中的 欄位。

`FIF_MODIFIERS`\
初始化/使用結構`bstrModifiers``FIELD_INFO`中的 欄位。

## <a name="remarks"></a>備註
這些值也作為參數傳遞給[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)方法,以指定要初始化[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)結構的欄位。

這些值還用於結構`dwFields`的成員`FIELD_INFO`中,以指示使用哪些欄位有效。

這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
