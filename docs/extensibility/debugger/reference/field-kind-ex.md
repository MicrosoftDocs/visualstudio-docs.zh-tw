---
description: 列舉 IDebugField 物件可以包含的其他欄位類型。
title: FIELD_KIND_EX |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75c1839987901edc9bc3571fa303ca0d3218a53c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059388"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
列舉 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件可以包含的其他欄位類型。 此列舉會擴充 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 列舉。

## <a name="syntax"></a>Syntax

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
欄位未包含擴充類型。

`FIELD_TYPE_EX_METHODVAR`\
欄位包含方法變數。

`FIELD_TYPE_EX_CLASSVAR`\
欄位包含類別變數。

## <a name="requirements"></a>規格需求
標頭： Sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
