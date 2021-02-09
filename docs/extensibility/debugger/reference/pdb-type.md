---
title: PDB_TYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df6a41801f4cce272d896776745ac0cc507d0e38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890015"
---
# <a name="pdb_type"></a>PDB_TYPE

此結構會指定取自 PDB 符號之欄位類型的相關資訊。

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
符號的來源應用程式識別碼。 這是用來唯一識別應用程式的實例。

`guidModule`\
包含此欄位之模組的 GUID。

`symid`\
對應至此欄位之符號的識別碼。

## <a name="remarks"></a>備註

當結構的[](../../../extensibility/debugger/reference/type-info.md) `dwKind` 欄位 `TYPE_INFO` 設定為 `TYPE_KIND_PDB` ([dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列舉) 中的值時，這個結構會顯示為 TYPE_INFO 結構中聯集的一部分。

## <a name="requirements"></a>規格需求

標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
