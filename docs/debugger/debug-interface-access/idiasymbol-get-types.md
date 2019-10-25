---
title: IDiaSymbol：： get_types |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739061"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
抓取此符號之編譯器特定類型的陣列。

## <a name="syntax"></a>語法

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>參數
 `cTypes`

在用來保存資料的緩衝區大小。

 `pcTypes`

脫銷傳回寫入的類型數目，或者，如果 `NULL` `types` 參數，則為可用的類型總數。

 `types[]`

脫銷要填入的陣列，其中包含代表此符號所有類型的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回 `S_FALSE` 或錯誤碼。

> [!NOTE]
> @No__t_0 的傳回值表示該屬性不適用於符號。

## <a name="see-also"></a>請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)