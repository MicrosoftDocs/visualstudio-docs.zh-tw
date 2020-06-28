---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2a4be91f2439c198ca7424ba13542c68d41c6b7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467663"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
依位址來抓取下一個符號。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>參數
 celt

在列舉值中要抓取的符號數目。

 rgelt

脫銷要以[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件填入的陣列，表示所需的符號。

 pceltFetched

脫銷傳回已提取枚舉器中的符號數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果沒有其他符號，則傳回 `S_FALSE` 。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會依提取的專案數來更新枚舉器位置。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)