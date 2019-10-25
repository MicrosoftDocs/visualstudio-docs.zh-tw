---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745256"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
描述位址對應中的專案。

## <a name="syntax"></a>語法

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>項目
`rva` 映射 A 中的相對虛擬位址（RVA）。

`rvaTo` 相對虛擬位址 `rva` 會對應到映射 B 中的。

## <a name="remarks"></a>備註
位址對應提供從一個影像版面配置（A）到另一個（B）的轉譯。 依 `rva` 排序的 `DiaAddressMapEntry` 結構陣列會定義位址對應。

若要將位址（`addrA`）在影像 A 中轉譯為位址，`addrB`，請在映射 B 中執行下列步驟：

1. 在地圖中搜尋 `e` 的專案，其中最大的 `rva` 小於或等於 `addrA`。

2. 設定 `delta = addrA - e.rva`。

3. 設定 `addrB = e.rvaTo + delta`。

    @No__t_0 結構的陣列會傳遞至[IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。

## <a name="requirements"></a>需求
標頭： dia2。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
