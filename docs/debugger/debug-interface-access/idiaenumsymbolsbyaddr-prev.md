---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 8fe7ced486524c7409532e140f48f841b5e55078
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467642"
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
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果沒有先前的符號，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會依提取的專案數來更新枚舉器位置。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)