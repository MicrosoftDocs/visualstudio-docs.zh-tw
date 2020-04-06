---
title: DEBUG_ADDRESS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe778ba3ed80930a4cd7b4fa1170f286b3ccf6ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737518"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
此結構表示位址。

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
進程識別碼。

`guidModule`\
包含此位址的模組的 GUID。

`tokClass`\
標識此位址的類或類型的權杖。

> [!NOTE]
> 此值特定於符號提供程式,因此除了作為類類型的標識符之外,沒有一般含義。

`addr`\
[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構,其中包含描述各個地址類型的結構聯合。 數`addr`值 。`dwKind` 來自[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚舉,它解釋了如何解釋聯合。

## <a name="remarks"></a>備註
此結構傳遞給要填充的[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法。

**警告 [僅限C++]**

如果`addr.dwKind``ADDRESS_KIND_METADATA_LOCAL`為 ,`addr.addr.addrLocal.pLocal`如果不是 空值,則`Release`必須呼叫 權杖指標:

```
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
{
    addr.addr.addrLocal.pLocal->Release();
}
```

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
