---
title: dwTYPE_KIND |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737189"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
指定如何解釋[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件的類型。

## <a name="syntax"></a>語法

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
[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)聯盟應被解釋為[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)結構。

`TYPE_KIND_PDB`\
聯合`TYPE_INFO`應解釋為[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)結構。

`TYPE_KIND_BUILT`\
聯合`TYPE_INFO`應解釋為[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)結構。

## <a name="remarks"></a>備註
此枚舉的值顯示在`dwKind`[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)結構的欄位中,用於確定如何解釋`type`聯合成員。 結構`TYPE_INFO`通過調用[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)方法返回。

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [取得類型資訊](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
