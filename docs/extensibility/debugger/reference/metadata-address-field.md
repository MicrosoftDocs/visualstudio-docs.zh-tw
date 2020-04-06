---
title: METADATA_ADDRESS_FIELD |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe9901ac9dab4a1ec4b5e8467f3063845dfb74f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714516"
---
# <a name="metadata_address_field"></a>METADATA_ADDRESS_FIELD

此結構表示類或結構的欄位的位址。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagMETADATA_ADDRESS_FIELD {
    _mdToken tokField;
} METADATA_ADDRESS_FIELD
```

```csharp
public struct METADATA_ADDRESS_FIELD {
    public int tokField;
}
```

## <a name="members"></a>成員

`tokField`\
欄位權杖的識別碼。

[C++]`_mdToken`是`typedef`32`int`位元的 。

## <a name="remarks"></a>備註

當`DEBUG_ADDRESS_UNION``ADDRESS_KIND_FIELD`結構欄位設置為[(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)舉中的值)`dwKind`時, 此結構是DEBUG_ADDRESS_UNION結構中的聯合的一部分。

## <a name="requirements"></a>需求

標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
