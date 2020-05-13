---
title: PDB_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714097"
---
# <a name="pdb_type"></a>PDB_TYPE

此結構指定有關從 PDB 符號獲取的欄位類型的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>成員

`ulAppDomainID`\
符號來自的應用程式的 ID。 這用於唯一標識應用程式的實例。

`guidModule`\
包含此欄位的模組的 GUID。

`symid`\
對應於此欄位的符號的 ID。

## <a name="remarks"></a>備註

當`TYPE_INFO``TYPE_KIND_PDB`結構欄位設定為[(dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)枚[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)舉中的值`dwKind`)時, 此結構在TYPE_INFO結構中顯示為聯合的一部分。

## <a name="requirements"></a>需求

標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
