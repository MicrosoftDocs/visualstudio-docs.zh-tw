---
title: FIELD_KIND_EX |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0c13d83f80b311838eca32945462c1f17ca23f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736873"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
枚舉[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件可以包含的其他類型的欄位。 此枚舉擴展[了FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)枚舉。

## <a name="syntax"></a>語法

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>欄位
`FIELD_KIND_EX_NONE`\
欄位不包含擴充類型。

`FIELD_TYPE_EX_METHODVAR`\
欄位包含方法變數。

`FIELD_TYPE_EX_CLASSVAR`\
欄位包含類變數。

## <a name="requirements"></a>需求
標題: Sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
