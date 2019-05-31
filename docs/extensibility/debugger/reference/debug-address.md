---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc25fb53db918486029e931a06a9e2de37f81c5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346302"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
此結構代表地址。

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
語彙基元，可識別的類別或此位址的類型。

> [!NOTE]
> 這個值是特定符號提供者也因此而不做為類別類型的識別項的一般意義。

`addr`\
A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構，其中包含可描述個別地址類型結構的聯集。 值`addr`。`dwKind` 來自[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別，其中說明如何解譯聯集。

## <a name="remarks"></a>備註
此結構會傳遞至[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)来填入的方法。

**警告 [C++只]**

如果`addr.dwKind`已`ADDRESS_KIND_METADATA_LOCAL`如果`addr.addr.addrLocal.pLocal`不是 null 的值，則您必須呼叫`Release`語彙基元的指標：

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>需求
標頭： sh.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
