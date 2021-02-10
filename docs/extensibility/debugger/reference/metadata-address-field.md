---
title: METADATA_ADDRESS_FIELD |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 686eeff2012c02442d166966fff32abc0b1cdf32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961972"
---
# <a name="metadata_address_field"></a>METADATA_ADDRESS_FIELD

此結構代表類別或結構的欄位位址。

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
欄位 token 的識別碼。

[C + +] `_mdToken` 是 `typedef` 32 位的 `int` 。

## <a name="remarks"></a>備註

當結構的[](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` 欄位 `DEBUG_ADDRESS_UNION` 設定為 `ADDRESS_KIND_FIELD` ([ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉) 中的值時，此結構就是 DEBUG_ADDRESS_UNION 結構中聯集的一部分。

## <a name="requirements"></a>規格需求

標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
