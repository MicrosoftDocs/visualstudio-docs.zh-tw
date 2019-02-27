---
title: 'Idiasymbol:: Get_isaggregated |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac588314b69c6be8b31cc5719a4be8add3cad33
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611031"
---
# <a name="idiasymbolgetisaggregated"></a>IDiaSymbol::get_isAggregated
擷取指定資料符號是否為彙總或符號; 集合的一部分的旗標編譯器會視為個別的實體的彙總的符號，但它們其實是單一的較大符號的一部分。

## <a name="syntax"></a>語法

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

[out]會傳回`TRUE`如果資料是從父符號; 分割符號的彙總的一部分，否則傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。

> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於符號。

## <a name="remarks"></a>備註
 [Idiasymbol:: Get_issplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)方法是`TRUE`父系的彙總的符號的符號。

## <a name="requirements"></a>需求

|需求|說明|
|-----------------|-----------------|
|標頭：|dia2.h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)