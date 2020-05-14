---
title: METADATA_ADDRESS_LOCAL |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3adf9ca5f679c7a526f10b1ee6c91d50dac52d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714481"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL

此結構表示作用域(通常是函數或方法)中的局部變數的位址。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagMETADATA_ADDRESS_LOCAL {
    _mdToken  tokMethod;
    IUnknown* pLocal;
    DWORD     dwIndex;
} METADATA_ADDRESS_LOCAL;
```

```csharp
public struct METADATA_ADDRESS_LOCAL {
    public int    tokMethod;
    public object pLocal;
    public uint   dwIndex;
}
```

## <a name="members"></a>成員

`tokMethod`\
本地變數的一部分的方法或函數的 ID。

[C++]`_mdToken`是`typedef`32`int`位元的 。

`pLocal`\
此結構表示的位址的權杖。

`dwIndex`\
可以是方法或函數中此局部變數的索引,也可以是其他一些值(特定於語言) 的索引。

## <a name="remarks"></a>備註

當`DEBUG_ADDRESS_UNION``ADDRESS_KIND_LOCAL`結構欄位設置為[(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)舉中的值)`dwKind`時, 此結構是DEBUG_ADDRESS_UNION結構中的聯合的一部分。

> [!WARNING]
> [僅C++]如果`pLocal`不是 null,則必須`Release`呼叫 權限`addr`( 是[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構中的欄位):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>需求

標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱

- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
