---
title: IDiaSymbol::get_classParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_classParent method
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 736d2150c2d19ba7ee7ee75bdb336fa6f0614a30
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613462"
---
# <a name="idiasymbolgetclassparent"></a>IDiaSymbol::get_classParent
擷取類別的父代符號的參考。

## <a name="syntax"></a>語法

```C++
HRESULT get_classParent ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)代表類別父系的符號的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是適用於符號。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v7.0|

## <a name="remarks"></a>備註
 可以是類別的父代的符號的類型所述[類別階層架構的符號類型](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)