---
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 58e00d55a26f3aaf771eed01135c62b607794876
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467754"
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

在要抓取的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件索引。 索引的範圍是0到 `count` -1，其中 `count` 是由[IDiaEnumSymbols：： get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)方法所傳回。

 符號

脫銷傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表所需的符號。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)