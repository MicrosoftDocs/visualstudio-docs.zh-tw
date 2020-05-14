---
title: METADATA_ADDRESS_RETVAL |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2437d10078eb623e063b3292d96ef9bb4a9cf64
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714266"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
此結構表示方法或函數的返回值。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagMETADATA_ADDRESS_RETVAL {
   _mdToken tokMethod;
   DWORD    dwCorType;
   DWORD    dwSigSize;
   BYTE     rgSig[10];
} METADATA_ADDRESS_RETVAL;
```

```csharp
public struct METADATA_ADDRESS_RETVAL {
   public int    tokMethod;
   public uint   dwCorType;
   public uint   dwSigSize;
   public byte[] rgSig;
}
```

## <a name="members"></a>成員
 `tokMethod`\
 此返回值所針對的方法的 ID。

 `dwCorType`\
 返回值的基本類型。 這是 .NET`CorElementType`框架 SDK corhdr.h 檔中定義的枚舉中的值。

 `dwSigSize`\
 返回值簽名的大小(存儲在中`rgSig`)。

 `rgSig`\
 組成返回值簽名的位元組。

## <a name="remarks"></a>備註
 當`DEBUG_ADDRESS_UNION``ADDRESS_KIND_RETVAL`結構欄位設置為[(ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)舉中的值)`dwKind`時, 此結構是DEBUG_ADDRESS_UNION結構中的聯合的一部分。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
