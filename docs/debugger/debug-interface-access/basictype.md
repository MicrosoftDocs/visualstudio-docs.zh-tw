---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745483"
---
# <a name="basictype"></a>BasicType
指定符號的基本類型。

## <a name="syntax"></a>語法

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>項目
btNoType 未指定任何基本類型。

btVoid 基本類型是 `void`。

btChar 基本類型是 `char` （C/C++ type）。

btWChar 基本類型是寬（Unicode）字元（`WCHAR`）。

btInt 基本類型為 `signed int` （C/C++ type）。

btUInt 基本類型為 `unsigned int` （C/C++ type）。

btFloat 基本類型是浮點數（`FLOAT`）。

btBCD 基本類型是二進位編碼的十進位數（`BCD`）。

btBool 基本類型是布林值（`BOOL`）。

btLong 基本類型是 `long int` （C/C++ type）。

btULong 基本類型是 `unsigned long int` （C/C++ type）。

btCurrency 基本類型為 currency。

btDate 基本類型是日期/時間（`DATE`）。

btVariant 基本類型是變數類型結構（`VARIANT`）。

btComplex 基本類型是複數。

btBit 基本類型為 bit。

btBSTR 基本類型是基本或二進位字串（`BSTR`）。

btHresult 基本類型是 `HRESULT`。

## <a name="remarks"></a>備註
此列舉中的值是由[IDiaSymbol：： get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
