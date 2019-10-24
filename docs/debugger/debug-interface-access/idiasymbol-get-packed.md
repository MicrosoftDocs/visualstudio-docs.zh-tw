---
title: IDiaSymbol：： get_packed |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 420ba5b56342b4b1d5b8e4c2756aa828e5fe53b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739529"
---
# <a name="idiasymbolget_packed"></a>IDiaSymbol::get_packed
抓取指定使用者定義資料類型（UDT）是否封裝的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_packed ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果 UDT 已封裝，則傳回 `TRUE`;否則，會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="remarks"></a>備註
 封裝表示 UDT 的所有成員都會盡可能地放在一起，而不會有中間填補來對齊記憶體界限。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)