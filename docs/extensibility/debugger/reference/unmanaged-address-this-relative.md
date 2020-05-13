---
title: UNMANAGED_ADDRESS_THIS_RELATIVE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea493170c7b422129485fcea4248981a2b506001
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713260"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
此結構表示相對於`this`指標(`Me`在可視化基本中)的位址。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagUNMANAGED_THIS_RELATIVE {
   DWORD dwOffset;
   DWORD dwBitOffset;
   DWORD dwBitLength;
} UNMANAGED_ADDRESS_THIS_RELATIVE;
```

```csharp
public struct UNMANAGED_THIS_RELATIVE {
   public uint dwOffset;
   public uint dwBitOffset;
   public uint dwBitLength;
}
```

## <a name="members"></a>成員
 `dwOffset`\
 與基本位置的位元組偏移量(例如,類vtable的開頭)。

 `dwBitOffset`\
 與基位的偏移(始終為 0,除非引用位欄位)。

 `dwBitLength`\
 表示地址的位數(除非引用位欄位,否則始終為 0)。

## <a name="remarks"></a>備註
 當`DEBUG_ADDRESS_UNION``ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`結構欄位設置為[(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)舉中的值)`dwKind`時, 此結構是DEBUG_ADDRESS_UNION結構中的聯合的一部分。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
