---
title: IDiaSymbol：： get_isAggregated |Microsoft Docs
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
ms.openlocfilehash: ee36d1901f7acb5bc7e41ac72b8dc03b15bc45c8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740288"
---
# <a name="idiasymbolget_isaggregated"></a>IDiaSymbol::get_isAggregated
抓取旗標，指定資料符號是否為匯總或符號集合的一部分。編譯器會將匯總的符號視為個別的實體，但它們實際上是單一較大符號的一部分。

## <a name="syntax"></a>語法

```C++
HRESULT get_isAggregated(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>參數
 `pFlag`

脫銷如果資料是從父符號分割之符號匯總的一部分，則傳回 `TRUE`。否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> `S_FALSE` 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 [IDiaSymbol：： get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)方法會針對做為匯總符號之父系的符號 `TRUE`。

## <a name="requirements"></a>需求

|需求|描述|
|-----------------|-----------------|
|標頭：|dia2。h|
|版本:|DIA SDK v8.0|

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)