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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3e4d5e4fcaad973ef21263e4eb3e5af6b42265e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856051"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
藉由依虛擬位址 (VA) 來執行查閱，以放置列舉值。

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

擴展傳回 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件，代表找到的符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果找不到符號，則會傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)