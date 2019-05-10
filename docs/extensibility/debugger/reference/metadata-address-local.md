---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10e94460dfd65294536fcb116099ba10c357d845
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461129"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL

此結構表示 （通常是函式或方法） 的範圍內的區域變數的位址。

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

方法或函式識別碼的本機變數是的一部分。

[C++]`_mdToken`是`typedef`適用於 32 位元`int`。

`pLocal`\

這個結構是表示其位址之語彙基元。

`dwIndex`\

可以是方法或函式或其他值 （語言特有） 中的這個本機變數的索引。

## <a name="remarks"></a>備註

此結構是中的等位的一部分[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)結構的時機`dwKind`欄位`DEBUG_ADDRESS_UNION`結構設定為`ADDRESS_KIND_LOCAL`(中的值[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列舉型別）。

> [!WARNING]
> [C++只]如果`pLocal`不是 null，則您必須呼叫`Release`語彙基元的指標 (`addr`是中的欄位[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構):
>
> ```cpp
> if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL && addr.addr.addrLocal.pLocal != NULL)
> {
>     addr.addr.addrLocal.pLocal->Release();
> }
> ```

## <a name="requirements"></a>需求

標頭： sh.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱

- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
