---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70265976e5c6e7c2b3f536f2b8648aaba44df528
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743850"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
依位址來抓取先前的符號。

## <a name="syntax"></a>語法

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在列舉值中要抓取的符號數目。

 rgelt

脫銷要填入的陣列，其中包含代表所需符號的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

 pceltFetched

脫銷傳回已提取枚舉器中的符號數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果沒有先前的符號，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會依提取的專案數來更新枚舉器位置。

## <a name="see-also"></a>請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)