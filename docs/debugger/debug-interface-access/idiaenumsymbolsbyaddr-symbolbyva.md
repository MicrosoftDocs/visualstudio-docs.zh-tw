---
title: IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: a0b97b30b6f19e367cfbae72be29b6d8961f4e1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833409"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
將列舉值的虛擬位址 (VA) 中執行查閱。

## <a name="syntax"></a>語法

```C++
HRESULT symbolByVA ( 
   DWORD**      virtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>參數
 virtualAddress

[in]虛擬位址。

 ppsymbol

[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示找到的符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 傳回`S_FALSE`如果找不到符號。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)