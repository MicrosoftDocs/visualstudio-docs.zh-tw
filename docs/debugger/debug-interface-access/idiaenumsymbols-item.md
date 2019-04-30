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
ms.openlocfilehash: 91c230f641612c099495c54db67da9c7e755cbdc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829436"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
透過索引中擷取的符號。

## <a name="syntax"></a>語法

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>參數
 索引

[in]索引[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)要擷取的物件。 索引是在範圍介於 0 到`count`-1，其中`count`會傳回[idiaenumsymbols:: Get_count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)方法。

 符號

[out]傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，表示所需的符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)