---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36bf189b8137c5a1a632dffd0b5a5d1641a9c24c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461689"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
抓取此符號之編譯器特定類型識別碼值的陣列。

## <a name="syntax"></a>語法

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>參數
 `cTypeIds`

在用來保存資料的緩衝區大小。

 `pcTypeIds`

脫銷傳回寫入的數目 `typeIds` ，或者，如果 `typeIds` 是 `NULL` ，則為可用的類型識別碼總數。

 `typeIds[]`

脫銷要填入類型識別碼的陣列。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` `S_FALSE` 或錯誤碼。

> [!NOTE]
> 的傳回值 `S_FALSE` 表示此屬性無法用於符號。

## <a name="see-also"></a>另請參閱
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)