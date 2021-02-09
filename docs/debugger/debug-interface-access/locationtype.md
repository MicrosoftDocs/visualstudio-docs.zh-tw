---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5aafc62f5920db70bd881bd3a541cfcfabfac360
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862343"
---
# <a name="locationtype"></a>LocationType
指出符號中包含的位置資訊種類。

## <a name="syntax"></a>Syntax

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>元素
`LocIsNull` 無法使用位置資訊。

`LocIsStatic` 位置是靜態的。

`LocIsTLS` 位置位於執行緒區域儲存區中。

`LocIsRegRel` 位置是註冊相關的。

`LocIsThisRel` 位置是 `this` 相對的。

`LocIsEnregistered` 位置位於註冊中。

`LocIsBitField` 位置位在位欄位中。

`LocIsSlot` Location 是 Microsoft 中繼語言 (MSIL) 位置。

`LocIsIlRel` 位置是 MSIL 相關的。

`LocInMetaData` 位置位於中繼資料中。

`LocIsConstant` 位置為常數值。

`LocTypeMax` 此列舉中的位置類型數目。

## <a name="remarks"></a>備註
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面可用的屬性會根據符號在影像檔案中的位置而定。 如需詳細資訊，請參閱 [符號位置](../../debugger/debug-interface-access/symbol-locations.md)。

呼叫 [IDiaSymbol：： get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) 方法時，會傳回此列舉中的值。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
