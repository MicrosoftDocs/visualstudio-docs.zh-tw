---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05475d2e6d48e7a8dacea834e5d7ca18c71d3260
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857304"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
描述位址對應中的專案。

## <a name="syntax"></a>Syntax

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>元素
`rva` 在影像 A 中 (RVA) 的相對虛擬位址。

`rvaTo` 相對虛擬位址 `rva` 會對應至影像 B 中的。

## <a name="remarks"></a>備註
位址對應會從一個影像配置提供轉譯， () 轉換成另一個 (B) 。 以排序的 `DiaAddressMapEntry` 結構陣列會 `rva` 定義位址對應。

若要轉譯位址，請 `addrA` 在影像 a 中的位址， `addrB` 在影像 B 中執行下列步驟：

1. 搜尋地圖中的專案，其 `e` 最大 `rva` 小於或等於 `addrA` 。

2. 設定 `delta = addrA - e.rva`。

3. 設定 `addrB = e.rvaTo + delta`。

    結構的陣列 `DiaAddressMapEntry` 會傳遞至 [IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 方法。

## <a name="requirements"></a>規格需求
標頭： dia2。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
