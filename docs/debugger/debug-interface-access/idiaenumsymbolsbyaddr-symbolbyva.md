---
title: IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByVA method
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f74f28dfd9b2a5ffdff4d6b5021dfbe4c7576bb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467586"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
藉由依虛擬位址（VA）執行查閱，來放置枚舉器。

## <a name="syntax"></a>語法

```C++
HRESULT symbolByVA ( 
   DWORD**      virtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>參數
 virtualAddress

在虛擬位址。

 ppsymbol

脫銷傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表找到的符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果找不到符號，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)