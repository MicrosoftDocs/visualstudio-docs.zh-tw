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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2fafbb25d52df6082736431727222c788d73476
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461214"
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

## <a name="elements"></a>元素
`LocIsNull`位置資訊無法使用。

`LocIsStatic`位置為靜態。

`LocIsTLS`位置是線上程區域儲存區中。

`LocIsRegRel`Location 是 register 相對的。

`LocIsThisRel`位置為 `this` -相對。

`LocIsEnregistered`位置在註冊中。

`LocIsBitField`位置在位欄位中。

`LocIsSlot`Location 是 Microsoft 中繼語言（MSIL）位置。

`LocIsIlRel`Location 是 MSIL 相對的。

`LocInMetaData`位置在中繼資料中。

`LocIsConstant`位置為常數值。

`LocTypeMax`這個列舉中的位置類型數目。

## <a name="remarks"></a>備註
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)介面可用的屬性取決於符號在影像檔案中的位置。 如需詳細資訊，請參閱[符號位置](../../debugger/debug-interface-access/symbol-locations.md)。

這個列舉中的值是由[IDiaSymbol：： get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)方法的呼叫所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [符號位置](../../debugger/debug-interface-access/symbol-locations.md)
