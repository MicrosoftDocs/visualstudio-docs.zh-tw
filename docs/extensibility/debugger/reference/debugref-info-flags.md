---
title: DEBUGREF_INFO_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737383"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
指定要檢索的有關調試引用物件的哪些資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>欄位
`DEBUGREF_INFO_NAME`\
初始化/使用結構`bstrName`中的欄位。

`DEBUGREF_INFO_TYPE`\
初始化/使用結構`bstrType`中的欄位。

`DEBUGREF_INFO_VALUE`\
初始化/使用結構`bstrValue`中的欄位。

`DEBUGREF_INFO_ATTRIB`\
初始化/使用結構`dwAttrib`中的欄位。

`DEBUGREF_INFO_REFTYPE`\
初始化/使用結構`dwRefType`中的欄位。

`DEBUGREF_INFO_REF`\
初始化/使用結構`pReference`中的欄位。

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
值欄位應包含此類型物件的自動展開值(如果可用)。

`DEBUGREF_INFO_NONE`\
指示未設置任何標誌。

`DEBUGREF_INFO_ALL`\
指示標誌的蒙版。

## <a name="remarks"></a>備註
這些標誌將傳遞給[Enum 子項](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)和[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)方法,以指示要初始化[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構的欄位。

用於`dwFields``DEBUG_REFERENCE_INFO`結構的成員,用於指示在返回結構時使用哪些欄位並有效。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
