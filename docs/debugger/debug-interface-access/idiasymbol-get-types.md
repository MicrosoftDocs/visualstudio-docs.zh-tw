---
description: 針對這個符號抓取編譯器特定類型的陣列。
title: IDiaSymbol：： get_types |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aec5db878c87ba257f1f83458d1ae742272a9b0f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160600"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
針對這個符號抓取編譯器特定類型的陣列。

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

在保存資料的緩衝區大小。

 `pcTypes`

擴展傳回寫入的類型數目，如果 `types` 參數為 `NULL` ，則為可用的類型總數。

 `types[]`

擴展要填入 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件的陣列，這些物件代表此符號的所有類型。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回 `S_FALSE` 錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示該符號無法使用該屬性。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
