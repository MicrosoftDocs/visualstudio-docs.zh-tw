---
title: dwTYPE_KIND |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e13d02cb08f957636a81bf4a985f1d7006b6c2ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908102"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
指定如何解讀 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件的類型。

## <a name="syntax"></a>Syntax

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>欄位
`TYPE_KIND_METADATA`\
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)聯集應解釋為[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)結構。

`TYPE_KIND_PDB`\
`TYPE_INFO`Union 應解讀為[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)結構。

`TYPE_KIND_BUILT`\
`TYPE_INFO`Union 應解讀為[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)結構。

## <a name="remarks"></a>備註
這個列舉的值會出現在 `dwKind` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 結構的欄位中，用來決定如何解讀等位 `type` 成員。 `TYPE_INFO` [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)方法的呼叫會傳回此結構。

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
