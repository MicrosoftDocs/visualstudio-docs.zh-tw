---
title: TYPE_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713321"
---
# <a name="type_info"></a>TYPE_INFO
此結構指定有關欄位類型的各種資訊。

## <a name="syntax"></a>語法

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>成員
 `dwKind`\
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)枚舉中確定如何解釋聯合的值。

 `type.typeMeta`\
 [僅C++]如果`dwKind``TYPE_KIND_METADATA`是 ,則包含[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)結構。

 `type.typePdb`\
 [僅C++]如果`dwKind``TYPE_KIND_PDB`是 ,則包含[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)結構。

 `type.typeBuilt`\
 [僅C++]如果`dwKind``TYPE_KIND_BUILT`是 ,則包含[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)結構。

 `type.unused`\
 未使用的填充。

 `type`\
 聯合的名稱。

 `unionmember`\
 [僅 C]將此情況編送到基於`dwKind`的相應結構類型。

## <a name="remarks"></a>備註
 此結構傳遞給填寫該結構的[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)方法。 結構內容的解釋方式基於欄位`dwKind`。

> [!NOTE]
> [僅C++]如果`dwKind`等`TYPE_KIND_BUILT`於 ,則`TYPE_INFO`在破壞 結構時必須釋放基礎[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。 藉由呼叫 `typeInfo.type.typeBuilt.pUnderlyingField->Release()` 即可達到此目的。

 [僅 C]下表顯示了如何解釋每種類型`unionmember`的成員。 該示例演示如何針對一種類型進行此操作。

|`dwKind`|`unionmember`解釋為|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>範例
 此示例演示如何解釋`unionmember`C#`TYPE_INFO`中 結構的成員。 此示例僅解釋一種類型`TYPE_KIND_METADATA`( ),但其他類型的解釋方式完全相同。

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [取得類型資訊](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
