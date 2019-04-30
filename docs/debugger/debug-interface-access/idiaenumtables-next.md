---
title: IDiaEnumTables::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15a9ebbd3a3993568e4b6496e04661a63290399e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832726"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
擷取指定的數目的列舉型別序列中的資料表。

## <a name="syntax"></a>語法

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>參數
 `celt`

[in]要擷取列舉值中的資料表數目。

 `rgelt`

[out]陣列，其中是要在以填滿[IDiaTable](../../debugger/debug-interface-access/idiatable.md)所需的資料表表示的物件。

 `pceltFetched`

[out]擷取列舉值中傳回資料表的數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`如果沒有更多的資料表。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)