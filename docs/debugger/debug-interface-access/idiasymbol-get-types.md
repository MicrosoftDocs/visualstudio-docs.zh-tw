---
title: IDiaSymbol：： get_types |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: d947eed08ba28cfdd68e2cd7d34998412fc8bc3a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461682"
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

脫銷傳回寫入的類型數目，或者，如果 `types` 參數為 `NULL` ，則為可用的類型總數。

 `types[]`

脫銷要填入的陣列，其中包含代表此符號所有類型的[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)