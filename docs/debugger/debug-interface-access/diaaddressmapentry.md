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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cae8159c893229f02e9598e932d7bc19efc2f4a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468676"
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

## <a name="elements"></a>元素
`rva`映射 A 中的相對虛擬位址（RVA）。

`rvaTo`相對虛擬位址 `rva` 會對應至映射 B 中的。

## <a name="remarks"></a>備註
位址對應提供從一個影像版面配置（A）到另一個（B）的轉譯。 `DiaAddressMapEntry`以排序的結構陣列會 `rva` 定義位址對應。

若要將位址（ `addrA` 在影像 A 中）轉譯為位址， `addrB` 請在映射 B 中執行下列步驟：

1. 在對應中搜尋 `e` 最大 `rva` 小於或等於的專案 `addrA` 。

2. 設定 `delta = addrA - e.rva`。

3. 設定 `addrB = e.rvaTo + delta`。

    結構的陣列 `DiaAddressMapEntry` 會傳遞至[IDiaAddressMap：： set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)方法。

## <a name="requirements"></a>需求
標頭： dia2。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
