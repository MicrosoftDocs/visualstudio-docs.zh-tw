---
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12766fe52f7f515b7ca411b17d58117e4e56cc9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743952"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
透過索引來抓取符號。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>參數
 索引

在要抓取的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件索引。 索引的範圍是0到 `count`-1，其中 `count` 是由[IDiaEnumSymbols：： get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)方法傳回。

 符號

脫銷傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表所需的符號。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)