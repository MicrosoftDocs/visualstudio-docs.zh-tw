---
description: 此結構代表位址。
title: DEBUG_ADDRESS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b250654f45f18adcfd9c52a6047b2b8798be75b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096365"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
此結構代表位址。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagDEBUG_ADDRESS {
    ULONG32             ulAppDomainID;
    GUID                guidModule;
    _mdToken            tokClass;
    DEBUG_ADDRESS_UNION addr;
} DEBUG_ADDRESS;
```

```csharp
public struct DEBUG_ADDRESS {
    public uint                ulAppDomainID;
    public Guid                guidModule;
    public int                 tokClass;
    public DEBUG_ADDRESS_UNION addr;
}
```

## <a name="members"></a>成員
`ulAppDomainID`\
處理序識別碼。

`guidModule`\
包含此位址之模組的 GUID。

`tokClass`\
識別此位址之類別或類型的權杖。

> [!NOTE]
> 這個值是符號提供者特有的值，因此除了做為類別類型的識別碼之外，並沒有一般意義。

`addr`\
[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構，其中包含描述個別網址類別型的結構聯集。 值 `addr` 。`dwKind` 來自 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 列舉，其說明如何解讀等位。

## <a name="remarks"></a>備註
此結構會傳遞至要填入的 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 方法。

**警告 [僅限 c + +]**

如果 `addr.dwKind` 為， `ADDRESS_KIND_METADATA_LOCAL` 而且如果不是 `addr.addr.addrLocal.pLocal` null 值，則您必須 `Release` 在 token 指標上呼叫：

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
