---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738641"
---
# <a name="locationtype"></a>LocationType
表示符號中包含的位置資訊類型。

## <a name="syntax"></a>語法

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

## <a name="elements"></a>項目
`LocIsNull` 位置資訊無法使用。

`LocIsStatic` 位置是靜態的。

`LocIsTLS` 位置是線上程區域儲存區中。

`LocIsRegRel` 位置是 register 相對的。

`LocIsThisRel` 位置是相對 `this`。

`LocIsEnregistered` 位置在註冊中。

`LocIsBitField` 位置在位欄位中。

`LocIsSlot` 位置是 Microsoft 中繼語言（MSIL）插槽。

`LocIsIlRel` 位置與 MSIL 相對。

`LocInMetaData` 位置是在中繼資料中。

`LocIsConstant` 位置為常數值。

`LocTypeMax` 此列舉中的位置類型數目。

## <a name="remarks"></a>備註
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面可用的屬性取決於符號在影像檔案中的位置。 如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)。

這個列舉中的值是由呼叫[IDiaSymbol：： get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
