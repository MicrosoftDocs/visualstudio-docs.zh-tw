---
title: METADATA_ADDRESS_METHOD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_METHOD
helpviewer_keywords:
- METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03a8e4850a2a18ec55655934618ba42a694b412d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347356"
---
# <a name="metadataaddressmethod"></a>METADATA_ADDRESS_METHOD
此結構表示的類別方法的位址。

## <a name="syntax"></a>語法

```cpp
typedef struct _tagMETADATA_ADDRESS_METHOD {
   _mdToken tokMethod;
   DWORD    dwOffset;
   DWORD    dwVersion;
} METADATA_ADDRESS_METHOD;
```

```csharp
public struct METADATA_ADDRESS_METHOD {
   public int  tokMethod;
   public uint dwOffset;
   public uint dwVersion;
}
```

## <a name="members"></a>成員
 `tokMethod`\
 方法的識別碼。

 [C++]`_mdToken`是`typedef`適用於 32 位元`int`。

 `dwOffset`\
 從類別的位移開始 （可以代表位移 vtable） 此方法。

 `dwVersion`\
 （這個值是唯一的符號提供者） 的方法版本。

## <a name="remarks"></a>備註
 此結構是中的等位的一部分[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構的時機`dwKind`欄位`DEBUG_ADDRESS_UNION`結構設定為`ADDRESS_KIND_METHOD`(中的值[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別）。

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)